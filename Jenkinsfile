pipeline {
	agent any;
	stages {
		stage('Build'){
			steps {
				echo "Build"
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
