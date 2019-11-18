pipeline {
  agent any
  stages {
    stage('Build') {
      agent any
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      agent any
      steps {
        sh 'mvn test'
        junit(allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml')
      }
    }

    stage('Deliver') {
      agent any
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }

  }
}