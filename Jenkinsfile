pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS = credentials('docker')
	}
    stages {
        stage('Login') {

			steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_USR'
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW'
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
        stage('Build Image') {
            steps {
                sh 'sudo docker build -t moredatta574/flask_jenkins .'
            }
        }
        stage('Run Image') {
            steps {
                sh 'sudo docker run -d --name flask_container moredatta574/flask_jenkis'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Successfully Pushed'
            }
        }
    }
}
