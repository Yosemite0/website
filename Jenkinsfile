pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        node {
          label 'Capstone_Test-Server'
        }

      }
      steps {
        build 'Capstone_Build_Project'
      }
    }

    stage('Test') {
      agent {
        node {
          label 'built-in'
        }

      }
      steps {
        build 'Capstone_Test_Project'
      }
    }

    stage('Deploy') {
      agent {
        node {
          label 'Capstone_Production'
        }

      }
      steps {
        build 'Capstone_Push-to-Production'
      }
    }

  }
}