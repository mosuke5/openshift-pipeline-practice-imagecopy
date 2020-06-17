pipeline {
  // pipelineを実行するagentの設定。yamlファイルで設定を渡せる
  // 可能な限りJenkinsfileにagentの設定をもたせたほうが自動化とGit管理が進むためおすすめ。
  agent {
    kubernetes {
      cloud 'openshift'
      yamlFile 'jenkins-agent-pod.yaml'
    }
  }

  stages {
    stage('Import image to ocp registry') {
      steps {
        sh 'skopeo --version'

        withCredentials([file(credentialsId: 'platform-operation-mysecret', variable: 'AUTHFILE')]) {
          sh "echo ${AUTHFILE}"
          sh "skopeo copy --authfile=${AUTHFILE} docker://centos:8 docker://image-registry.openshift-image-registry.svc:5000/user1-application/my-image:v1"
        }
      }
    }
  }
}
