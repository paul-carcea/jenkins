//DECLARATIVE
pipeline {
		//agent any
		agent { 
			//docker { image 'maven:3.6.3' }
			any { image 'node:18-alpine3.15' }
		}
		stages {
			stage('Build') {
				steps {
					//sh 'mvn --version'
					sh 'node --version'
					echo "Build"
				}
			}
			stage('Test') {
				steps {
					echo "Test"
				}
			}
			stage('Integration-Test') {
				steps {
					echo "Integration-Test"
				}
			}
		}
		post {
			always {
				echo "Im awesome. I run always."
			}
			success {
				echo "I run when you are succesful."
			}
			failure {
				echo "I run when you fail."
			}
		}
}
