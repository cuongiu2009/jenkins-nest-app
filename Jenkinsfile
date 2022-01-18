pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t advanced-network-jenkins:1.1 .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		
		stage('View Images') {

			steps {
				sh 'docker images'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push https://hub.docker.com/advanced-network-jenkins'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
