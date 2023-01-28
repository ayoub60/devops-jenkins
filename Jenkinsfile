pipeline {
	agent any
	//agent { docker { image 'node:13.8'} }
	environnement {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		$PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Build'){
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
		stage('Test'){
			steps {
				echo "Test"
			}
		}
		stage('Integration test'){
			steps {
				echo "Integration test"
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
