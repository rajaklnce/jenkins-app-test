pipeline {
  agent any
  
  stages {
    stage('first step'){
      steps {
        sh 'cat README.md'
        println('success')
      }
    }
    stage('pull request comment'){
      steps{ 
        script {
          def PULL_REQUEST = env.CHANGE_ID
          withCredentials([string(credentialsId: 'jenkins-rajaklnce', variable: 'GITHUB_TOKEN')]) {
            sh "curl -s -H \"Authorization: token ${GITHUB_TOKEN}\" -X POST -d '{\"body\": \"This is my first test comment from jenkins\"}' \"https://github.com/api/v3/repos/***/${env.GIT_URL.tokenize("/")[-1].tokenize(".")[0]}/issues/${PULL_REQUEST}/comments\""
            }
        }
      }
    }
  }
}
