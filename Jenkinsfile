pipeline {
  agent any
  tools {
        maven '3.8.2' 
        jdk 'JAVA_8'
    }
  
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
            sh 'mvn clean install'
            sh '''
            curl -s -H "Authorization: token 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" \
 -X POST -d '{"body": "Your Message to Comment"}' \
 "https://api.github.com/repos/rajaklnce/jenkins-app-test/issues/${CHANGE_ID}/comments"
            '''
          }
        }
      }
    }
    post {
      failure {
        script {
          sh '''
            curl -s -H "Authorization: token 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" \
 -X POST -d '{"body": "failed"}' \
 "https://api.github.com/repos/rajaklnce/jenkins-app-test/issues/${CHANGE_ID}/comments"
            '''
        }
      }
    }
  }
