pipeline {

    agent any

    // stages{
    //     stage('Build'){
    //         steps{
    //             echo "Building..."
    //         }
    //     }
    //     stage('Test'){
    //         steps{
    //             echo "Testing..."
    //         }
    //     }
    //     stage('Deploy'){
    //         steps{
    //             echo "Deploying..."
    //         }
    //     }
    // }   
    // environment {
    //     DOCKER_CREDENTIALS_ID = 'cfee730d-55df-4401-b36a-dcb2cf03fe48' // ID for Docker Hub credentials stored in Jenkins
    //     // EC2_SSH_CREDENTIALS_ID = ''  // ID for SSH credentials for EC2 instance stored in Jenkins
    //     DOCKER_IMAGE_NAME = 'myreact-app'    // The name of your Docker image
    //     DOCKER_TAG = 'version1'             // Tag for your Docker image
    //     DOCKER_REPO = 'vishnudhaya/frontend-app-jenkins-server' // Docker Hub repository name (no URL)
    //     // EC2_HOST = ''           // EC2 instance public IP
    //     EC2_USER = 'ec2-user'                 // SSH user for EC2
    // }
    // stages {
    //     stage('Build Docker Image') {
    //         steps {
    //             script {
    //                 // Build Docker image
    //                 docker.build("${DOCKER_REPO}:${DOCKER_TAG}")
    //             }
    //         }
    //     }
    //     stage('Push Docker Image') {
    //         steps {
    //             script {
    //                 // Push Docker image to Docker Hub
    //                 docker.withRegistry('https://index.docker.io/v1/', "${DOCKER_CREDENTIALS_ID}") {
    //                     docker.image("${DOCKER_REPO}:${DOCKER_TAG}").push("${DOCKER_TAG}")
    //                 }
    //             }
    //         }
    //     }
    // }
    environment {
        DOCKER_CREDENTIALS_ID = 'cfee730d-55df-4401-b36a-dcb2cf03fe48' // ID for Docker Hub credentials stored in Jenkins
        DOCKER_IMAGE_NAME = 'myreact-app'    // The name of your Docker image
        DOCKER_TAG = 'version1'             // Tag for your Docker image
        DOCKER_REPO = 'vishnudhaya/frontend-app-jenkins-server' // Docker Hub repository name (no URL)
        EC2_USER = 'ec2-user'               // SSH user for EC2 (if needed in future stages)
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image ${DOCKER_REPO}:${DOCKER_TAG}"
                    docker.build("${DOCKER_REPO}:${DOCKER_TAG}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    echo "Pushing Docker image ${DOCKER_REPO}:${DOCKER_TAG}"
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                        docker.image("${DOCKER_REPO}:${DOCKER_TAG}").push(DOCKER_TAG)
                    }
                }
            }
        }
    }
}