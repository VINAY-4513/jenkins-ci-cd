pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t jenkins-demo .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f jenkins-demo || true'
                sh 'docker run -d --name jenkins-demo jenkins-demo'
            }
        }

        stage('Test') {
            steps {
                sh 'docker exec jenkins-demo nginx -t'
            }
        }
    }
}
