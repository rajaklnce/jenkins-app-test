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
            pullRequest.comment('This PR is highly illogical..')
          }
        }
      }
    }
  }
