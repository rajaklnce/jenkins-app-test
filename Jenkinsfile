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
        script {
          sh '''
            curl -s -H "Authorization: token <GITHUb personal token>" \
 -X POST -d '{"body": "BUILD FAILED"}' \
 "https://api.github.com/repos/rajaklnce/jenkins-app-test/issues/${CHANGE_ID}/comments"
            '''
        }
      }
      success {
        script {
          sh '''
            curl -s -H "Authorization: token <GITHUb personal token>" \
 -X POST -d '{"body": "BUILD SUCCESS"}' \
 "https://api.github.com/repos/rajaklnce/jenkins-app-test/issues/${CHANGE_ID}/comments"
            '''
        }
      }
    }
  }
