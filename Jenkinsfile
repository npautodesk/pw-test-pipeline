pipeline {
   agent any

   tools { nodejs 'nodejs' }
   // agent { docker { image 'mcr.microsoft.com/playwright:v1.44.1-jammy' } }
   stages {
      stage('Checkout') {
            steps {
            // Clone the repository
            git branch: 'main', url: 'https://github.com/npautodesk/pw-test-pipeline.git'
            }
      }
      stage('e2e-tests') {
         steps {
            sh 'su - jenkins -s /bin/bash'
            sh 'npx playwright install-deps'
            sh 'npm ci'
            sh 'npx playwright test'
         }
      }
   }
}
