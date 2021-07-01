pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn compile'
        fileExists 'pom.xml'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn clean test'
      }
    }

    stage('Deploy') {
      steps {
        sh 'mvn package'
      }
    }

    stage('Archive') {
      steps {
        archiveArtifacts '**/target/spock-lizard-1.0.jar'
      }
    }

  }
}