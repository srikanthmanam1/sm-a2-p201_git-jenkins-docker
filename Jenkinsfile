pipeline {
    agent any

    environment {
        //DOCKERHUB_USER = credentials('dockerhub-username')  // Jenkins credential ID
        IMAGE_NAME = "jenkins"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/srikanthmanam1/sm-a2-p201_git-jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Run Container for Tests') {
            steps {
                script {
                    dockerImage.run('-d -p 5000:5000')
                }
            }
        }

        //stage('Push to Docker Hub') {
        //    when {
        //        branch 'main'
        //    }
        //    steps {
        //        script {
        //            docker.withRegistry('', 'dockerhub-username') {
        //                dockerImage.push("${BUILD_NUMBER}")
        //                dockerImage.push("latest")
        //            }
        //        }
        //    }
        //}
    }

    post {
        always {
            sh 'docker ps -q --filter ancestor=$IMAGE_NAME | xargs -r docker stop'
        }
    }
}
