pipeline {
  agent any
  tools {
        maven '3.8.2' 
        jdk 'JAVA_8'
    }
  
  stages {
    stage('First Stage'){
      steps {
        sh 'cat README.md'
        println('success')
      }
    }
    stage('BUILD'){
      steps{  
        script {
            sh 'mvn clean install'
          }
        }
      }
    }
    post {
      failure {
        ## Taking password token from jenkins creds for security purpose
        withCredentials([usernamePassword(credentialsId: 'github-token-creds', passwordVariable: 'pass-token', usernameVariable: 'user')]) {
          script {
            sh '''
              curl -s -H "Authorization: token $pass-token" \
   -X POST -d '{"body": "BUILD FAILED"}' \
   "https://api.github.com/repos/rajaklnce/jenkins-app-test/issues/${CHANGE_ID}/comments"
              '''
          }
        }
      }
      success {
        ## Taking password token from jenkins creds for security purpose
        withCredentials([usernamePassword(credentialsId: 'github-token-creds', passwordVariable: 'pass-token', usernameVariable: 'user')]) {
          script {
            sh '''
              curl -s -H "Authorization: token $pass-token" \
   -X POST -d '{"body": "BUILD SUCCESS"}' \
   "https://api.github.com/repos/rajaklnce/jenkins-app-test/issues/${CHANGE_ID}/comments"
              '''
          }
        }
      }
    }
  }
