pipeline {
  agent any
  tools {
    maven 'Local Maven'
  }
  stages {
    stage('checkout') {
      steps {
        git branch: '${BRANCH_NAME}', credentialsId: 'athulk918', url: 'git@github.com:athulk918/newmaven.git'
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
    stage("deploy"){
            steps{
                sshagent(['deploy_user']) {
                 sh "scp -o StrictHostKeyChecking=no target/myProject-1.0-SNAPSHOT.jar ubuntu@35.174.204.206:/opt/apache-tomcat-8.5.65/webapps"
                                    }
            }
    }
  }
}
