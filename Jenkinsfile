pipeline {
    agent {
        label 'workers'
    }

    stages {
        stage ('Checkout') {
            steps {
                checkout scm
            }
        }

        stage ('Build Docker image') {
            steps {
                sh "docker build -t netcore-hello-world ."

                sh "docker tag netcore-hello-world dockerjenkinsg/netcore-hello-world:1"

                sh "docker login --username dockerjenkinsg --password Registry_for_Jenkins"

                sh "docker push dockerjenkinsg/netcore-hello-world:1"

                sh "docker rmi netcore-hello-world dockerjenkinsg/netcore-hello-world:1"
            }
        }
    }
}
