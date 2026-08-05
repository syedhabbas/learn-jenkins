
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                    echo "Building Pipeline...!"
                    npm --version
                '''
            }
        }
         stage('Test') {
            steps {
                echo 'Testing Pipeline...!'
            }
        }
    }
}

