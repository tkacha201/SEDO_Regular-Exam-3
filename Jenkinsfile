pipeline {
    agent any

    triggers {
        // Run automatically every 5 minutes (simulating push detection)
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build .NET Application') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run Unit and Integration Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        success {
            echo 'Build and Tests completed successfully!'
        }
        failure {
            echo 'Build or Tests failed.'
        }
    }
}
