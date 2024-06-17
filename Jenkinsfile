pipeline {
    agent any

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
