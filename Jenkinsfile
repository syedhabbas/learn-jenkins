
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
            // npm ci, creates node_modules folder with fresh installed files.
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
            agent {
                docker {
                    image "node:18-alpine"
                    reuseNode true
                }
            }
            steps {
                sh '''
                echo 'Testing Pipeline...!'
                test -f build/index.html
                npm test
                '''
            }
        }
    }
    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}

