pipeline {
	agent { docker { image 'maven:3.6.3'} }
	stages {
		stage('Build'){
			steps {
				sh "mvn --version"
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
