pipeline {
  agent any
  stages {
    stage('Build') {
      agent any
      steps {
        git(url: 'https://github.com/yff144/simple-java-maven-app', branch: 'master')
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
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }

  }
}