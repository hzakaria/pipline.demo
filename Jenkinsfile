pipeline {
    agent any
    tools {
        maven 'Maven 3.8.7'
    }
    stages {

    stage('Clone Repo') {
        // for display purposes
        // Get some code from a GitHub repository
        steps {
         git url: 'https://github.com/hzakaria/pipline.demo.git'
                  //  credentialsId: 'springdeploy-user',
                  //  branch: 'main'
        }

     }
    stage('Build docker') {
       steps {
       script{
         docker.build("pipline.demo:${env.BUILD_NUMBER}")
         }
         }
    }
    stage('Deploy docker'){
       steps {
       script{
          echo "Docker Image Tag Name: ${pipline.demo${env.BUILD_NUMBER}}"
          sh "docker stop pipline.demo || true && docker rm pipline.demo² || true"
          sh "docker run --name pipline.demo -d -p 8081:8080 pipline.demo:${env.BUILD_NUMBER}"
          }
          }
    }  }

}


