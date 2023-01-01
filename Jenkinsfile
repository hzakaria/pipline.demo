pipeline {
    agent any
    tools {
        maven 'maven_3.8.7'
    }

    stage('Clone Repo') {
        // for display purposes
        // Get some code from a GitHub repository
        git url: 'https://github.com/hzakaria/pipline.demo.git'
          //  credentialsId: 'springdeploy-user',
          //  branch: 'main'
     }
    stage('Build docker') {
         dockerImage = docker.build("pipline.demo:${env.BUILD_NUMBER}")
    }
    stage('Deploy docker'){
          echo "Docker Image Tag Name: ${pipline.demo${env.BUILD_NUMBER}}"
          sh "docker stop pipline.demo || true && docker rm pipline.demo² || true"
          sh "docker run --name pipline.demo -d -p 8081:8080 pipline.demo:${env.BUILD_NUMBER}"
    }

}


