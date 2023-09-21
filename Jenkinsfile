pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '40', artifactNumToKeepStr: '40'))
        ansiColor('xterm')
        timestamps()
        disableConcurrentBuilds()
    }
    stages {
        stage('SSH Server') {
            steps {
                sshagent(credentials : ['docker']) {
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@43.204.101.80 ./deploy.sh $BUILD_NUMBER'
                }
            }
        }
    }
}
