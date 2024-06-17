pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/playwright:latest'
            args '-u root' // to run as root and install packages if needed
        }
    }
    environment {
        CI = 'true' // Setting the CI environment variable
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm ci' // Clean install npm dependencies
            }
        }
        stage('Run Playwright Tests') {
            steps {
                sh 'npx playwright install' // Install the Playwright browsers
                script {
                    def items = ['one', 'two', 'three']
                    items.each { item ->
                        echo "suite: ${item}"
                        sh 'npx playwright test' // Run the Playwright tests
                    }
                }
            }
        }
    }
}
