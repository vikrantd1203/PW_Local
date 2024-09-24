
pipeline {
    agent any
    tools {
        nodejs "nodejs-playwright"
    }

    stages {
        stage('setup') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9', localConfig: [localOptions: '', localPath: '']) {
                {
                    //sh 'curl -o BrowserStackLocal-darwin-x64.zip "https://www.browserstack.com/browserstack-local/BrowserStackLocal-darwin-x64.zip"'
                    // sh 'wget "https://www.browserstack.com/browserstack-local/BrowserStackLocal-linux-x64.zip"'
                    // sh 'unzip BrowserStackLocal-darwin-x64.zip'
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon start'
                    // sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon stop'
                }
            }
            }
            }

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
                    // sh 'npm run sample-local-test'
                }
            }
        }

    }

    post {
        always {
            script {
                // Stop BrowserStack Local after the tests
                sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon stop'
            }
        }
    }
}
}

