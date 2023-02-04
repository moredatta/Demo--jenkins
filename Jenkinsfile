pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS = credentials('docker')
	}
    stages {
        stage('Login') {

			steps {
                bat "cmd /c echo $DOCKERHUB_CREDENTIALS_USR"
               bat "cmd /c echo $DOCKERHUB_CREDENTIALS_PSW" 
				bat "cmd echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW" 
			}
		}
        stage('Build Image') {
            steps {
                bat "cmd docker build -t moredatta574/flask_jenkins ."
            }
        }
        stage('Run Image') {
            steps {
                bat "cmd docker run -d  -p 9090:9191 --name flask_container moredatta574/flask_jenkins"
            }
        }
        
        stage('Test') {
            steps {
                echo 'Successfully Pushed'
            }
        }
    }
}
