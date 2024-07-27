pipeline {
  agent any
  stages {
    stage('git pull') {
      steps {
        // https://github.com/SeongJuMoon/Bkv2_sub_gitops will replace by sed command before RUN
        git url: 'https://github.com/SeongJuMoon/Bkv2_sub_gitops', branch: 'main'
      }
    }
    stage('k8s deploy'){
      steps {
        withKubeConfig([credentialsId: 'k8s-auth', serverUrl: 'https://192.168.1.10:6443']) {
          sh 'kubectl apply -f deployment.yaml'
        }
      }
    }
  }
}
