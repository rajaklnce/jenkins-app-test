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
          withGroovy(tool: '3.8.2'){
            sh 'mvn clean install'
          }
        }
      }
    }
  }
}
