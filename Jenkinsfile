pipeline {
	agent { docker { image 'node:13.8'} }
	stages {
		stage('Build'){
			steps {
				sh "node --version"
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
