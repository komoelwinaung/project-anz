pipeline {
agent any
environment {
AWS_ACCOUNT_ID="461805207***"
AWS_DEFAULT_REGION="ap-southeast-1"
IMAGE_REPO_NAME="jenkins-pipeline"
IMAGE_TAG="image06"
REPOSITORY_URI = "${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}"
            }

stages {
// Logging into the AWS ECR from Jenkins EC2
stage('Logging into AWS ECR') {
steps {
script {
sh "/bin/aws/aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"
                              }

}
}
 
// Cloning Git from Jenkins EC2
stage('Cloning Git') {
steps {
checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/komoelwinaung/project-anz.git']]])     
}
}

// Building Docker Image for Deployment
stage('Building image') {
steps{
script {
dockerImage = docker.build "${IMAGE_REPO_NAME}:${IMAGE_TAG}"
}
}
}

// Pushing this Image to AWS ECR
stage('Pushing to ECR') {
steps {
script {
sh "docker tag ${IMAGE_REPO_NAME}:${IMAGE_TAG} ${REPOSITORY_URI}:$IMAGE_TAG"
sh "docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:$IMAGE_TAG"
}
}

}
}
}
