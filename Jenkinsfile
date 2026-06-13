pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t springboot-demo:latest .'
            }
        }

        stage('Run') {
            steps {
                sh '''
                docker rm -f springboot-demo || true
                docker run -d --name springboot-demo -p 8081:8080 springboot-demo:latest
                '''
            }
        }
    }
}
