pipeline {
    agent any
    environment {
        IMAGE_NAME = "srikanthmanam/sm-app1"
        IMAGE_TAG = "latest"
    }
    
    stages {
        /*stage('Checkout') {
            steps {                
                git branch: 'gjdf_ex1', url 'https://github.com/srikanthmanam1/sm-a2-p201_git-jenkins-docker.git'
            }
        }*/
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker --version'
                    sh 'docker build -t $IMAGE_NAME:$IMAGE_TAG .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                echo 'Run Docker Container'
                script {
                    sh 'docker run --rm $IMAGE_NAME:$IMAGE_TAG'
                }
            }
        }
        // OPTIONAL: push to Docker Hub
        /*
        stage('Login & Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-credentials',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh "echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin"
                    sh "docker push $IMAGE_NAME:$IMAGE_TAG"
                }
            }
        }
        */
    }
    post {
        always {
            echo 'Post Action'
            //sh 'docker ps -q --filter ancestor=$IMAGE_NAME | xargs -r docker stop'
            sh 'docker stop $IMAGE_NAME:$IMAGE_TAG'
            sh 'docker ps -a --filter "status=exited"'
            sh 'docker rmi $IMAGE_NAME:$IMAGE_TAG || true'
            //sh 'docker container prune -f'
        }
    }
}
