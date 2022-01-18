pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t advanced-network-jenkins:latest .'
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
		
		stage('Docker Tag') {

			steps {
				sh 'docker tag advanced-network-jenkins datkira/advanced-network-jenkins'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push datkira/advanced-network-jenkins'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
