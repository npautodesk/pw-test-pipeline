pipeline {
    agent any

    stages {
        stage('Conditional Loop Example') {
            steps {
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
