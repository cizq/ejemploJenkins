pipeline {
    agent any
    environment{
        DOCKERHUB_CREDS = credentials('Pagman')
    }
    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
                sh 'ls *'
            }
        }
        stage('Build Image') {
            steps {
                //Aquí debes poner tu github
		sh 'docker build -t ejemplojenkins .'
            }
        }
        stage('DockerHUB Login') {
            steps {
                
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'                
                }
            }
        stage('Docker Push') {
            steps {
		//Aquí debes poner tu github
                sh 'sudo docker push $DOCKERHUB_CREDS_USR/dockerhub'
                }
            }
        }
    post {
		always {
			sh 'docker logout'
		}
	 }
    }

