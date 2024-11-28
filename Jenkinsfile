pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install project dependencies
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                // Build the project
                sh 'npm run build'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                // Deployment steps (example: copying files to a server)
                sshPublisher(publishers: [
                    sshPublisherDesc(
                        configName: 'MyServer',
                        transfers: [sshTransfer(sourceFiles: '**/build/**', remoteDirectory: '/var/www/html')],
                        verbose: true
                    )
                ])
            }
        }
    }
}
