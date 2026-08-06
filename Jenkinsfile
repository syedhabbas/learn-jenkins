
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
            // npm test, will create folder test-results/junit.xml & in post block we will make junit report. 
            steps {
                sh '''
                echo 'Testing Pipeline...!'
                test -f build/index.html
                npm test
                '''
            }
        }
         stage ('E2E') {
            agent {
                docker {
                    image "mcr.microsoft.com/playwright:v1.62.0-noble"
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo 'E2E Pipeline...'
                    npm install serve
                    node_modules/.bin/serve  -s build &
                    sleep 10
                    npx playwright test
                '''
            }
        }
    }
    post {
        always {
            junit 'jest-results/junit.xml'
        }
    }
}