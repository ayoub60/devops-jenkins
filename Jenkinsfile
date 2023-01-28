pipeline {
	agent any
	//agent { docker { image 'node:13.8'} }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout'){
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "$PATH"
				echo "BUILD NUMBER = $env.BUILD_NUMBER"
				echo "BUILD ID = $env.BUILD_ID"
				echo "JOB NAME = $env.JOB_NAME"
				echo "BUILD TAG = $env.BUILD_TAG"
			}
		}
		stage('Compile'){
			steps {
				sh "mvn clean compile"
			}
		}	
		stage('Test'){
			steps {
				sh "mvn test"
			}
		}
		stage('Integration test'){
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package'){
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage('Buil image'){
			steps {
				//"docker build -t ayoub6000/repotest:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("ayoub6000/repotest:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push'){
			steps {
				script {
					dockerImage.withRegistry('','dockerhub'){
					   dockerImage.push();
					   dockerImage.push('latest');	
					}
				}
			}
		}
	}
	post {
		always {
			echo "always"
		}
		success {
			echo 'succes'
		} 
		failure {
			echo 'failure'
		}
	}
	
}
