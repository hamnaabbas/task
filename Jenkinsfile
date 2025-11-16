pipeline {
    agent any

    stages {
        stage('Build Info') {
            steps {
                echo "Build #${env.BUILD_NUMBER} started"
                echo "Triggered at: ${new Date()}"
                if (currentBuild.rawBuild.getCauses()[0].toString().contains("GitHub")) {
                    echo "Triggered by GitHub Webhook"
                }
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/noorulain-nn/task.git'
            }
        }

        stage('Install') {
            steps { bat 'npm install' }
        }

        stage('Test') {
            steps { bat 'npm test' }
        }
    }
}

