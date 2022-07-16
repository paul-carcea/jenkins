//DECLARATIVE
pipeline {
		agent any
			//agent { docker { image 'maven:3.6.3' } }
			//agent { docker { image 'node:18-alpine3.15' } }
		environment {
			dockerHome = tool 'MyDocker'
			mavenHome = tool 'MyMaven'
			PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
		}
		stages {
			stage('Checkout') {
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
			stage('Compile') {
				steps {
					sh "mvn clean compile"
				}
			}
			stage('Test') {
				steps {
					sh "mvn test"
				}
			}
			stage('Integration-Test') {
				steps {
					sh "mvn failsafe:integration-test failsafe:verify"
				}
			}
			stage('Package') {
				steps {
					sh "mvn package -DskipTests" //jar file
				}
			}
			stage('Build Docker Image') {
				steps {
					//"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
					script {
						dockerImage = docker.build("in28min/currency-exchange-devops:${env.BUILD_TAG}")
					}
				}
			}
			stage('Push Docker Image') {
				steps {
					script {
						docker.withRegistry('', 'dockerhub'){ //se alege id-ul pus din Jenkins
							dockerImage.push();
							dockerImage.push('latest');
						}
					}
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
