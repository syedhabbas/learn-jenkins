
pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image "node:18-alpine"
                }
            }
            steps {
                sh '''
                    echo "Building Pipeline...!"
                    npm --version
                '''
            }
        }
         stage('Test') {
            steps {
                sh '''
                echo 'Testing Pipeline...!'
                '''
            }
        }
    }
}

