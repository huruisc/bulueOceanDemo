pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '/home/maven/apache-maven-3.6.3/bin/mvn clean install'
        junit 'target/surefire-reports/TEST-*.xml'
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            junit 'target/surefire-reports/TEST-*.xml'
          }
        }

        stage('dependency-check') {
          steps {
            dependencyCheck()
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'this is a deploying ....'
      }
    }

  }
  triggers {
    pollSCM('H/3 * * * *')
  }
}