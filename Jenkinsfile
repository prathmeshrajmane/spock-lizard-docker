pipeline {
  agent any
  stages {
    stage('log tool versions') {
      parallel {
        stage('log tool versions') {
          steps {
            sh '''mvn --version
git --version
java -version'''
          }
        }

        stage('check for pom') {
          steps {
            fileExists 'pom.xml'
          }
        }

      }
    }

    stage('Build with Maven') {
      steps {
        sh 'mvn compile test package'
      }
    }

    stage('post build steps') {
      steps {
        writeFile(file: 'status.txt', text: 'hey it worked')
      }
    }

  }
}