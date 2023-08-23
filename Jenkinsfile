pipeline {
  agent any

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/JaeOh-00/test-jenkins.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'admin', url: 'https://github.com/JaeOh-00/test-jenkins.git')], contextPath: null, war: '/var/lib/jenkins/workspace/maven_project/target/hello-world.war'
      }
    }
  }
}
