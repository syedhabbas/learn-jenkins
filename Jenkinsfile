
pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image "node:18-alpine"
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Building Pipeline...!"
                    npm --version
                    npx --version
                    node --version
                    ls -lap
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

