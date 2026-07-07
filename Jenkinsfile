pipeline {

    agent any

    stages {

        stage('Clone Source') {
            steps {
                echo "Source code downloaded from GitHub"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop myapp || true
                docker rm myapp || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                --name myapp \
                -p 5000:5000 \
                myapp
                '''
            }
        }

    }

}
