pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Build Step: Check files in workspace'
                bat 'dir'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying Student.html and style.css to IIS folder"

                bat "xcopy /Y Student.html ${DEPLOY_DIR}\\"
                bat "xcopy /Y style.css ${DEPLOY_DIR}\\"
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
            echo 'Pipeline finished successfully! Visit: http://localhost/Student.html'
        }

        failure {
            echo 'Pipeline failed! Check build logs.'
        }
    }
}