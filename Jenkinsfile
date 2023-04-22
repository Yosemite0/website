properties([pipelineTriggers([githubPush()])])
pipeline {
    agent any
    stages{
        stage('Build') {
          steps {
            build job: 'Capstone_Build_Project'
          }
        }        
        stage('Test') {
          steps {
            build job: 'Capstone_Test_Project'
          }
        }
        
        stage('Deploy') {
          when {
            branch "master"
          }
          steps {
            build job: 'Capstone_Push-to-Production'
          }
        }
    }
}
