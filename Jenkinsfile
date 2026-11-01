
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Docker Image'
                bat 'docker build -t myapp .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Application'
                bat 'docker run --rm myapp python -m unittest test_app.py'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application'
                bat 'docker rm -f myapp-container || exit /b 0'
                bat 'docker run -d -p 5000:5000 --name myapp-container myapp'
            }
        }
    }
}
