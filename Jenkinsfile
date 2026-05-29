pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out Jenkins First Project source code...'
            }
        }

        stage('Validate Files') {
            steps {
                echo 'Validating required project files...'

                bat '''
                if exist welcome.html (
                    echo welcome.html file found
                ) else (
                    echo welcome.html file missing
                    exit /b 1
                )

                if exist design.css (
                    echo design.css file found
                ) else (
                    echo design.css file missing
                    exit /b 1
                )

                if exist message.js (
                    echo message.js file found
                ) else (
                    echo message.js file missing
                    exit /b 1
                )
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Starting build process for Jenkins First Project...'
                bat 'dir'
                echo 'Build completed successfully.'
            }
        }

        stage('Automated Testing') {
            steps {
                echo 'Running automated validation tests...'

                bat '''
                findstr /i "<html" welcome.html
                if %errorlevel% neq 0 (
                    echo HTML validation failed
                    exit /b 1
                ) else (
                    echo HTML validation passed
                )

                findstr /i "Jenkins First Project" welcome.html
                if %errorlevel% neq 0 (
                    echo Project title validation failed
                    exit /b 1
                ) else (
                    echo Project title validation passed
                )
                '''
            }
        }

        stage('Automation Summary') {
            steps {
                echo 'Pipeline orchestration completed successfully.'
                echo 'Pipeline stages executed: Checkout, Validate Files, Build, Automated Testing, Automation Summary.'
                echo 'Automated build and validation steps passed successfully.'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Jenkins First Project pipeline completed successfully.'
        }

        failure {
            echo 'FAILED: Jenkins First Project pipeline failed. Check console output.'
        }
    }
}