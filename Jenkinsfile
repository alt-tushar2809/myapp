pipeline {
    agent any
    environment {
        DOCKER_REGISTRY = '<your-dockerhub-username>'
        IMAGE_NAME = 'my-app'
        KUBE_NAMESPACE = 'default'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/alt-tushar2809/myapp.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_REGISTRY/$IMAGE_NAME:${BUILD_NUMBER} .'
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-credentials', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push $DOCKER_REGISTRY/$IMAGE_NAME:${BUILD_NUMBER}'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl apply -f deployment.yaml
                kubectl set image deployment/my-app \
                my-app=$DOCKER_REGISTRY/$IMAGE_NAME:${BUILD_NUMBER} -n $KUBE_NAMESPACE
                '''
            }
        }
    }
}
