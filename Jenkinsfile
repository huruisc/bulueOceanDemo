pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '/home/maven/apache-maven-3.6.3/bin/mvn clean install'
      }
    }

    stage('Test') {
      steps {
        junit 'target/surefire-reports/TEST-*.xml'
      }
    }

    stage('Dependency-check') {
      steps {
        dependencyCheck(additionalArguments: '--failOnCVSS 10 --format ALL', odcInstallation: 'dependency-check')
        dependencyCheckPublisher(pattern: 'dependency-check-report.xml')
      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            echo 'this is a deploying ....'
          }
        }

        stage('Archive') {
          steps {
            echo 'Product archived!'
          }
        }

      }
    }

  }
  triggers {
    pollSCM('H/3 * * * *')
  }
}