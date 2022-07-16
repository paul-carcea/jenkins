//DECLARATIVE
pipeline {
		agent any
			//agent { docker { image 'maven:3.6.3' } }
			//agent { docker { image 'node:18-alpine3.15' } }
		environment {
			dockerHome = tool 'MyDocker'
			mavenHome = tool 'MyMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages {
			stage('Build') {
				steps {
					sh 'mvn --version'
					sh 'docker version'
					echo "Build"
					echo "$PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
					echo "BUILD_TAG - $env.BUILD_TAG"
					echo "BUILD_URL - $env.BUILD_URL"
					echo "JOB_NAME - $env.JOB_NAME"

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
