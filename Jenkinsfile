pipeline {
    agent {
        label 'docker'
    }

    stages {

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t m7/docker-jenkins -f DOCKERFILE.dev .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    env.DOCKER_BUILDKIT = "1"
                    sh 'docker run -e CI=true m7/docker-jenkins npm run test'
                }
            }
        }

    }
}