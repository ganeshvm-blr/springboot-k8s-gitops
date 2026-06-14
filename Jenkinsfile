pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh './mvnw clean verify sonar:sonar -Dsonar.projectKey=springboot-demo -DskipTests'
                }
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
                docker stop springboot-demo || true

                docker ps -q --filter "publish=8081" | xargs -r docker stop

                docker run -d --name springboot-demo -p 8081:8080 springboot-demo:latest
                '''
            }
        }
    }
}
