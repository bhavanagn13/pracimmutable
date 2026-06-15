pipeline{
	agent any
	tools{
		maven 'Maven'
	}
	
	stages {
		stage('Build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('test'){
			steps{
				sh 'mvn test'
		}
		}
		
		stage('Run Application'){
			steps{
				sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
			}
		}
	}
	
	post{
		success{
			echo 'Build, test and execution successful'
		}
		failure{
			echo 'Pipeline failed'
		}
		always{
			junit 'target/surefire-reports/*.xml'
		}
	}
}
				
