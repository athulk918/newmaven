pipeline {
  agent any
  tools {
    maven 'Local Maven'
  }
  stages {
    stage('checkout') {
      steps {
        git credentialsId: 'athulk918', url: 'git@github.com:athulk918/newmaven.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package'
      }
    }
  }
}
