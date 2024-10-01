
pipeline {
    agent any
    tools {
        nodejs "nodejs-playwright"
    }

    stages {
        stage('setup1') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9', localConfig: [localOptions: '--force-local', localPath: '']) {
                    // sh 'curl -o BrowserStackLocal-darwin-x64.zip "https://www.browserstack.com/browserstack-local/BrowserStackLocal-darwin-x64.zip"'
                    // sh 'wget "https://www.browserstack.com/browserstack-local/BrowserStackLocal-linux-x64.zip"'
                    // sh 'unzip BrowserStackLocal-darwin-x64.zip'
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon start'
                    echo 'First Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'First Completed'
                }
            }
        }

        stage('setup2') {
            steps{
                browserstack
                 {
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon start'
                    echo 'Second Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'Second Completed'
                }
            }
        }
        stage('setup3') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9') {
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon start'
                    echo 'Third Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'Third Completed'
                }
            }
        }
        stage('setup4') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9') {
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon start'
                    echo 'Fourth Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'Fourth Completed'
                }
            }
        }
        stage('setup5') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9') {
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon start'
                    echo 'Fifth Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'Fifth Completed'
                }
            }
        }
        stage('setup6') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9', localConfig: []) {
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon start'
                    echo 'Sixth Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'Sixth Completed'
                }
            }
        }
    }

    post {
        always {
            script {
                // Stop BrowserStack Local after the tests
                echo 'Stopping BStack Binary'
                sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --daemon stop'
            }
        }
    }
}

