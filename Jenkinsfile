pipeline {
    agent any

    environment {
        DOTNET_VERSION = '6.0'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify .NET SDK') {
            steps {
                bat 'dotnet --info'
            }
        }

        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build application') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            echo '✅ Build and test completed.'
        }
        failure {
            echo '❌ Build or test failed.'
        }
    }
}
