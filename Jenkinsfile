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
        def comment = pullRequest.comment('This PR is highly illogical..')
      }
    }
  }
}
