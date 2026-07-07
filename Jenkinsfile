pipeline {

    agent any

    stages {

        stage('Git Checkout') {
            steps {
                git 'https://github.com/edbinbaby/DevOps-App.git'
            }
        }


        stage('Docker Build') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }


        stage('Docker Deploy') {
            steps {
                sh '''
                docker stop devops || true
                docker rm devops || true

                docker run -d \
                --name devops \
                -p 5000:5000 \
                devops-app
                '''
            }
        }

    }
}
