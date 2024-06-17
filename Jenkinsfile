pipeline {
    agent any

    environment {
        CI = 'true' // Setting the CI environment variable
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                git branch: 'main', url: 'https://github.com/ni3pandharpatte/pw-del-me-repo.git'
            }
        }
        stage('Install Node.js') {
            steps {
                // Install Node.js if it's not already installed
                sh 'apt-get install -y nodejs'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install npm dependencies
                sh 'npm ci'
            }
        }
        stage('Compile TypeScript') {
            steps {
                // Compile TypeScript to JavaScript
                sh 'npx tsc'
            }
        }
        stage('Run Playwright Tests') {
            steps {
                // Install the Playwright browsers
                sh 'npx playwright install'
                // Run the Playwright tests
                sh 'npx playwright test'
            }
        }
    }

    post {
        always {
            // Archive test results or perform any cleanup here
            archiveArtifacts artifacts: 'test-results/**', allowEmptyArchive: true
            junit 'test-results/**/*.xml' // Adjust this if you have junit reports
        }
    }
}
