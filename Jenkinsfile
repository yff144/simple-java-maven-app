pipeline {
  agent any
  stages {
    stage('Build') {
      agent any
      steps {
        git 'https://github.com/jenkins-docs/simple-java-maven-app.git'
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