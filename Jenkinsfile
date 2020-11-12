pipeline{
	agent any
	
	triggers { 
		pollSCM('H/3 * * * *') 
	}
	
	stages{	    
		stage('Build'){
			steps{
				sh '/home/maven/apache-maven-3.6.3/mvn clean install'
				junit 'target/surefire-reports/TEST-*.xml'
			}
		}
		stage('Test'){
			steps{
				junit 'target/surefire-reports/TEST-*.xml'
			}
		}
		stage('Deploy'){
			steps{
				echo "this is a deploying ...."
			}
		}
	}
}
