pipeline {
    agent any

    environment {
        IMAGE_NAME = "springboot-demo"
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ganeshvm-blr/springboot-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f springboot-demo || true
                docker run -d --name springboot-demo -p 8081:8080 $IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }
    }
}
