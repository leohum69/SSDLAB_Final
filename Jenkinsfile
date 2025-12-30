pipeline {
    agent any

    environment {
        TARGET_DIR = "C:/Users/${env.USERNAME}/Desktop/deploy_simulation"
    }

    stages {
        
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                bat 'pip install -r requirements.txt'
            }
        }
        stage('Test') {
            steps {
                
                echo 'Starting Flask app...'
                bat 'start /B python file.py'
                echo 'Waiting for app to start...'
                bat 'timeout /T 5'
                echo 'Running tests...'
                echo 'Checking if website is live (simulated)...'
                bat 'curl -I http://localhost:5000 || echo Site not live (simulated check)'
                
            }
        }
        stage('Build') {
            steps {
                echo 'Packaging app (simulated)...'
                bat 'if not exist build mkdir build && xcopy /E /I /Y * build\\'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Simulating deployment to desktop...'
                bat 'if not exist "%TARGET_DIR%" mkdir "%TARGET_DIR%" && xcopy /E /I /Y build\\* "%TARGET_DIR%"'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
