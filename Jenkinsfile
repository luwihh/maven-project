pipeline {
	/* A Declarative Pipeline */
	agent any
	
	stages {
						
		stage('Build') {
			steps {
				sh 'mvn clean package'
			}
			post {
				success {
					echo 'Now Archiving...'
					archiveArtifacts artifacts: '**/target/*.war'
				}
			}
		}
		stage('Deploy to Staging') {
			/* Agent section could go here as well */
			steps {

			}
		}
	}
}