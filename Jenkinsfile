
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
                    ls -lap
                    node --version
                    npm --version
                    npx --version
                    npm ci
                    npm run build
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

