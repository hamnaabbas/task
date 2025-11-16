pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/<your-username>/<your-app>.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Lint & Test') {
            steps {
                bat 'npm run lint'
                bat 'npm test'
            }
        }

        stage('Archive Build') {
            steps {
                bat 'tar -a -c -f build.zip .'
                archiveArtifacts artifacts: 'build.zip', fingerprint: true
            }
        }
    }

    post {
        success {
            echo "Email sent to team@example.com"
        }
        failure {
            echo "Build failed! Email sent to team@example.com"
        }
    }
}

