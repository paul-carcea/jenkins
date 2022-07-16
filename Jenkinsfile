//DECLARATIVE
pipeline {
		//agent any
		agent { 
			any { image 'maven:3.8.6' }
		}
		stages {
			stage('Build') {
				steps {
					sh 'mvn --version'
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
