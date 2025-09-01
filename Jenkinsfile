pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kalyanpd/my-python-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mypythonapp:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                    docker rm -f mypythonapp || true
                    docker run -d -p 5000:5000 --name mypythonapp mypythonapp:latest
                '''
            }
        }
    }
}

