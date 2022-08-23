pipeline {
    agent {
        label 'XYZ'
        }
    environment {
		DOCKERHUB_CREDENTIALS = credentials('DockerHub')
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
                sh 'sudo docker build -t desaiakshay92/flask_jenkins .'
            }
        }
        stage('Run Image') {
            steps {
                sh 'sudo docker run -d --name flask_container desaiakshay92/flask_jenkis'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Successfully Pushed'
            }
        }
    }
}
