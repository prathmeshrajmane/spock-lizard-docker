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
        script {
           sh ''' sudo git config remote.origin.url 'https://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@github.com/prathmeshrajmane/spock-lizard-docker.git'

sudo git tag -fa v${BUILD_NUMBER} -m 'Release version ${BUILD_NUMBER}' 

sudo git push origin v${BUILD_NUMBER}
                      '''
        }
      }
      
    }

    stage('Archive') {
      steps {
        archiveArtifacts '**/target/spock-lizard-1.0.jar'
      }
    }

    
  }
}
