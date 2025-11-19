pipeline {
    agent any
    options {
        timestamps()
    }
    stages {
        stage('Hello 1') {
            steps {
                echo 'Hello World 1'
                 sh 'docker --version'
            }
        }
        stage('Hello 2') {
            steps {
                echo 'Hello World 2'
                sh 'docker run hello-world'
            }
        }
        stage('Hello 3') {
            steps {
                echo 'Hello World 3'
                sh 'docker images'
            }
        }
        stage('Hello 4') {
            steps {
                echo 'Hello World 4'
                sh 'docker ps'
            }
        }
        stage('Hello 5') {
            steps {
                echo 'Hello World 5'
            }
        }
    }
}
