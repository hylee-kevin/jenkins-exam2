pipeline {
    environment {
    imagename = "backend"
    jenkinsProject = 'calculator-webapp-backend'
  }

    agent any
    stages {

        stage('Git Staging'){

            steps{

                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-credd', url: 'https://github.com/hylee-kevin/jenkins-exam2.git']]])

            }
        }


        stage('Build image and Run image ') {

            steps{
                sh 'sudo su - jenkins -s/bin/bash'
                //sh 'sudo docker stop $imagename'
                //sh 'sudo docker rm $imagename'
                //sh 'sudo docker rmi $imagename'
                sh 'sudo docker image build -t  $imagename .'

            }

        }
        
        stage('Run image ') {

            steps{
                //sh 'sudo docker stop $imagename
                //sh 'sudo docker rm $imagename
                sh 'sudo docker run -p5000:5000 --restart=always --name $imagename  -itd $imagename'

            }

        }
        

        
    }
}
