pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '40', artifactNumToKeepStr: '40'))
        timestamps()
        disableConcurrentBuilds()
    }
    stages {
        stage('SSH Server') {
            steps {
                sshagent(credentials : ['docker']) {
                    sh 'ssh -o StrictHostKeyChecking=no ubuntu@13.232.239.79 ./deploy.sh $BUILD_NUMBER'
                }
            }
        }
    }
}
