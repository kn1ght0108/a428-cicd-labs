node {
    docker.image('node:lts-buster-slim').withRun('-p 3000:3000')
    environment {
        NODE_OPTIONS = '--openssl-legacy-provider'
    }
        
    stage('Build') {
        sh 'npm install'
        sh 'npm run build'
    }
    
    stage('Test') {
        sh './jenkins/scripts/test.sh'
    }

    stage('Deliver') {
        sh './jenkins/scripts/deliver.sh'
        input message: 'Finished using the website? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
    }
}