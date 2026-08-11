pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                git branch: 'main',
                    url: 'https://github.com/Disha-Hambire/jenkins-html-cicd.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Build completed successfully!'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the web application...'
                bat 'if exist index.html (echo index.html found) else (exit /b 1)'
                bat 'if exist style.css (echo style.css found) else (exit /b 1)'
                bat 'if exist script.js (echo script.js found) else (exit /b 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying website...'
                bat 'if not exist C:\\jenkins-deploy mkdir C:\\jenkins-deploy'
                bat 'xcopy /Y /I *.html C:\\jenkins-deploy\\'
                bat 'xcopy /Y /I *.css C:\\jenkins-deploy\\'
                bat 'xcopy /Y /I *.js C:\\jenkins-deploy\\'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}