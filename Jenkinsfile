pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'test_pipeline',
                    url: 'https://github.com/DmitryMaxim18/4Docker.git'
                echo 'Hello World'
                sh 'ls'
            }
        }
        stage('Preparing') {
            steps {
                sh 'python3 -m pip install -r req.txt'
            }
        }
        stage('Run') {
            steps {
                sh 'pytest -n 5 -m shallow --junitxml=result.xml'
            }
            post {
                always {
                    junit 'result.xml'
                }
            }
        }
    }
}
