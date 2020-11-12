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
    stage('Package') {
            sh "'mvn' -Dmaven.test.skip=true package"
            archive 'target/*.jar'
       }		
		stage('Deploy'){
			steps{
				echo "this is a deploying ...."
			}
		}
	}
}
