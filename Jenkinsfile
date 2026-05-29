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

                sh '''
                if [ -f welcome.html ]; then
                    echo "welcome.html file found"
                else
                    echo "welcome.html file missing"
                    exit 1
                fi

                if [ -f design.css ]; then
                    echo "design.css file found"
                else
                    echo "design.css file missing"
                    exit 1
                fi

                if [ -f message.js ]; then
                    echo "message.js file found"
                else
                    echo "message.js file missing"
                    exit 1
                fi
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Starting build process for Jenkins First Project...'
                sh 'ls -la'
                echo 'Build completed successfully.'
            }
        }

        stage('Automated Testing') {
            steps {
                echo 'Running automated validation tests...'

                sh '''
                grep -i "<html" welcome.html
                if [ $? -ne 0 ]; then
                    echo "HTML validation failed"
                    exit 1
                else
                    echo "HTML validation passed"
                fi

                grep -i "Jenkins First Project" welcome.html
                if [ $? -ne 0 ]; then
                    echo "Project title validation failed"
                    exit 1
                else
                    echo "Project title validation passed"
                fi
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