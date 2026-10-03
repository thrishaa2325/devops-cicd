pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-app:latest .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker image inspect cicd-app:latest > /dev/null'
                echo 'Docker image built successfully!'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh 'ansible-playbook -i ansible/inventory ansible/deploy.yml'
            }
        }

    }
}
