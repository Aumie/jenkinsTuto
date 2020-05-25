pipeline {
    agent { docker 'gcc:latest' }

    stages {
        stage('Build') {
            steps {
                sh 'make --version' 
                sh 'make check || true' 
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                sh 'make publish'
            }
        }
    }
}
