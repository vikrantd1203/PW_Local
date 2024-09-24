pipeline {
    agent any


    tools {
        nodejs "nodejs-playwright"
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Install Playwright and other Node.js dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Run Playwright Tests') {
            steps {
                script {
                    // Run Playwright tests with BrowserStack
                    sh 'npm run sample-test'
                }
            }
        }
    }

}
