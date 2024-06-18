pipeline {
   agent { docker { image 'mcr.microsoft.com/playwright:v1.44.1-jammy' } }
   stages {
      stage('Checkout') {
            steps {
                // Clone the repository
                git 'https://github.com/npautodesk/pw-test-pipeline.git' // Replace with your repo URL
            }
      }
      stage('e2e-tests') {
         steps {
            sh 'npm ci'
            sh 'npx playwright test'
         }
      }
   }
}
