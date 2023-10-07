pipeline {
    agent any

    stages {
        stage('Clone Git Repo') {
            steps {
               git credentialsId: '35f8a50e-8e09-47aa-8d92-8b91b73f22c4', url: 'https://github.com/SrinivasBattina/snakegame.git'
            }
        }
         stage('Build Docker Image') {
            steps {
               echo "Creating Docker Image"
               sh 'docker build -t project1:$BUILD_NUMBER .'
            }
        }
         stage('Run Docker image') {
            steps {
               echo "Running docker image"
               sh 'docker stop $(docker ps -aq)'
               sh 'docker rm $(docker ps -aq)'
               sh 'docker run -d -p 80:80 --name snake-game project1:$BUILD_NUMBER'
            }
        }
    }
}
