pipeline {
    agent any

    environment {
        IMAGE_NAME = "nimnajudy/nginx-web:v1"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Build Successful"'
            }
        }

        stage('Deploy') {
            steps {
                dir('ansible') {
                    sh 'ansible-playbook -i inventory playbook.yml'
                }
            }
        }
    }
}