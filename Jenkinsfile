properties([pipelineTriggers([githubPush()])])
pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
        steps {
            checkout([
             $class: 'GitSCM',
             branches: [[name: '*/master'],[name: '*/develop']],
             userRemoteConfigs: [[
                url: 'https://github.com/Yosemite0/website.git',
                credentialsId: '',
             ]]
            ])
        }
    }
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
