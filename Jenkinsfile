pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore the project') {
            when {
                anyOf {
                    branch 'develop'
                    branch 'feature'
                }
            }
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build the project') {
            when {
                anyOf {
                    branch 'develop'
                    branch 'feature'
                }
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test the project') {
            when {
                anyOf {
                    branch 'develop'
                    branch 'feature'
                }
            }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
