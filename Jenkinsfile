pipeline {

	agent any

	stages {
	
		stage('Build') {
			steps {
				echo "Building..."
				sh 'sudo su'
				sh 'docker run -v `pwd`:/build damoncheng/public:debian-build-v1'

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
