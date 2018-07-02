pipeline {

	agent any

	stages {
	
		stage('Build') {
			steps {
				echo "Building..."
				sh 'sudo su'
				sh 'make html'
			}
		}

		stage('Test') {
			steps {
				echo "Testing..."
			}
		}

		stage('Deploy') {
			steps {
				echo "Deploying..."
			}
		}
	
	}
	post {
	
		failure {
			mail to: "snhellogg@gmail.com", subject: 'The Pipeline failed :(', body: 'hello jenkins two'
		}
	
	}

}
