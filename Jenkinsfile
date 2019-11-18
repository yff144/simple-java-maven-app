pipeline {
  agent any
  stages {
    stage('Build') {
      agent any
      steps {
        git 'https://github.com/yff144/simple-java-maven-app'
        sh 'sh \'mvn -B -DskipTests clean package\''
      }
    }

    stage('Test') {
      agent any
      steps {
        sh 'sh \'mvn test\''
        junit(allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml')
      }
    }

    stage('Deliver') {
      steps {
        sh 'sh \'./jenkins/scripts/deliver.sh\''
      }
    }

  }
}