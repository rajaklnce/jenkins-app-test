pipeline {
  agent any
  tools {
        maven '3.8.2' 
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
          sh 'mvn clean install'
        }
      }
    }
  }
