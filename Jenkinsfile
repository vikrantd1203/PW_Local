pipeline {
    agent any
    tools {
        nodejs "nodejs-playwright"
    }

    stages {
        stage('setup1') {
            steps{
                browserstack(credentialsId: '833c8871-ab95-4280-9199-9c2469b191d9') {
                    // sh 'curl -o BrowserStackLocal-darwin-x64.zip "https://www.browserstack.com/browserstack-local/BrowserStackLocal-darwin-x64.zip"'
                    // sh 'wget "https://www.browserstack.com/browserstack-local/BrowserStackLocal-linux-x64.zip"'
                    // sh 'unzip BrowserStackLocal-darwin-x64.zip'
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --local-identifier t1 --daemon start'
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --local-identifier t2 --daemon start'
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --local-identifier t3 --daemon start'
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --local-identifier t3 --daemon start'
                    sh './BrowserStackLocal --key $BROWSERSTACK_ACCESS_KEY --local-identifier t3 --daemon start'
                    echo 'First Setup'
                    sh 'npm install'
                    sh 'npm run sample-test'
                    echo 'First Completed'
                }
            }
        }
    }
    post {
        always {
            script {
                // Stop BrowserStack Local after the tests
                echo 'Stopping BStack Binary'
            }
        }
    }
}