pipeline {
    agent any
    stages {
        stage("checkout") {
            steps {
                checkout scm
            }
        }
        stage("Build Image") {
            steps {
                sh 'docker build -t my-node-app:1.0 .'
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'erramlysalma2', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
                    sh "docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD"
                    sh "docker tag my-node-app:1.0 erramlysalma/my-node-app:1.0"
                    sh "docker push erramlysalma/my-node-app:1.0"
                    sh "docker logout"
                }
            }
        }
    }
}


