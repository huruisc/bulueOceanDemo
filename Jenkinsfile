pipeline{
	agent any
	
	triggers { 
		pollSCM('H/3 * * * *') 
	}
	
	stages{	    
		stage('Test'){
			steps{
				sh 'mvn clean install'
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
