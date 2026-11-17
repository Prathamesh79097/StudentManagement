pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Cloning project from GitHub...'

                git branch: 'main',
                    url: 'YOUR_GITHUB_REPOSITORY_URL'
            }
        }

        stage('Build') {
            steps {
                echo 'Build Step: Check files in workspace'
                bat 'dir'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying Home.html to IIS folder"

                bat "xcopy /Y Home.html ${DEPLOY_DIR}\\"
            }
        }

        stage('Run HTTP Server (Optional Test)') {
            steps {
                echo 'Skipping HTTP server (use IIS instead)'

                // For testing, you can use:
                // bat 'python -m http.server 8000'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully! Visit: http://localhost/Home.html'
        }

        failure {
            echo 'Pipeline failed! Check build logs.'
        }
    }
}