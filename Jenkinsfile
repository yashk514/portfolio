
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
                sh 'ls -la'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Portfolio Files...'
                sh 'test -f index.html'
                sh 'test -f style.css'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Portfolio...'

                sh '''
                    sudo cp index.html /var/www/html/
                    sudo cp style.css /var/www/html/
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
