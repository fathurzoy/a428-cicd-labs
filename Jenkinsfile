pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'rm -rf node_modules'
                sh 'rm -f package-lock.json'
                sh 'rm -f yarn.lock'
                sh 'npm cache clean --force'
                sh 'npm config rm proxy'
                sh 'npm config rm https-proxy'
                sh 'npm cache verify'
                sh 'npm set registry=https://registry.npmjs.org/'
                sh 'npm install' 
            }
        }
    }
}