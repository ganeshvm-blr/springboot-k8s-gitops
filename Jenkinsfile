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
                    sh 'mvn clean verify sonar:sonar -DskipTests'
                }
            }
        }
stage('Docker Login') {
    steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
            sh '''
            echo $PASS | docker login -u $USER --password-stdin
            '''
        }
    }
}
        stage('Docker Build') {
            steps {
                sh 'docker build -t springboot-demo:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh '''
                    echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                    docker tag springboot-demo:latest ganeshvmblr/springboot-cicd:latest
                    docker push ganeshvmblr/springboot-cicd:latest
                    '''
                }
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
