pipeline {
    agent {
        docker {
            image 'node:lts-bullseye-slim'
            args '-p 3000:3000'
        }
    }
    stages {
        stage('Install Yarn') {
            steps {
                script {
                    // Create a directory for local npm packages
                    sh 'mkdir -p .npm-global'
                    
                    // Set npm prefix to the local directory
                    sh 'npm config set prefix=$WORKSPACE/.npm-global'

                    // Add npm binaries to the PATH
                    sh 'export PATH=$WORKSPACE/.npm-global/bin:$PATH'

                    // Install Yarn locally
                    sh 'npm install yarn'

                    // Use Yarn for the rest of the pipeline
                    sh 'yarn install'
                }
            }
        }
    }
}
