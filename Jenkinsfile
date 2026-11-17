
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
                    if not exist C:\\portfolio-deploy mkdir C:\\portfolio-deploy

                    copy /Y index.html C:\\portfolio-deploy\\
                    copy /Y style.css C:\\portfolio-deploy\\
                '''
            }
        }

        stage('Open Website') {
            steps {
                echo 'Opening Portfolio Website...'
                bat 'start "" "C:\\portfolio-deploy\\index.html"'
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
