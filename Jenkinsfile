pipeline {

	agent any

	stages {
	
		stage('Build') {
			steps {
				echo "Building..."
				sh 'sudo su'
				sh 'docker run -v `pwd`:/build damoncheng/python:jessie'

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
