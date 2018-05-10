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
								timeout(time:5, unit:'DAYS') {
									input message: 'Approve Staging Deployment?'
								}
								build job: 'deploy-to-staging' 
							}
							post {
								success {
									echo 'Code deployed to Production'
								}
								
								failure {
									echo 'Deployment failed'
								}
							}
						}
					}
				}