pipeline {
    agent any
    
    environment {
        PATH = "/opt/homebrew/bin:/usr/local/bin:${env.PATH}"
    }

    stages {
        stage('Build_docker_image') {
        steps {
            sh 'docker build -t my-web-app:${BUILD_NUMBER} .'
        }
        }

    stage('Run_Container') {
        steps {
            sh '''
            docker stop my-web-container || true
            docker rm my-web-container || true
            docker run -d -p 9080:80 --name my-web-container my-web-app:${BUILD_NUMBER}
            '''
        }
    }
    }
}