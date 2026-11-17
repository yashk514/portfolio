
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yashk514/portfolio.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Portfolio Website...'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Portfolio Files...'

                bat '''
                    if not exist index.html exit /b 1
                    if not exist style.css exit /b 1
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Portfolio...'

                bat '''
                    if not exist C:\\inetpub\\wwwroot mkdir C:\\inetpub\\wwwroot

                    copy /Y index.html C:\\inetpub\\wwwroot\\
                    copy /Y style.css C:\\inetpub\\wwwroot\\
                '''
            }
        }
    }

    post {
        success {
            echo 'Portfolio deployed successfully!'
        }

        failure {
            echo 'Pipeline execution failed!'
        }
    }
}
