pipeline {
    agent { 
        node {
            label 'docker-agent-python'
        }
    }
    stages {
        stage('Build') {
           steps {
                echo "Building..."
                sh '''
                cd myapp
                export PYTHONUSERBASE=$(pwd)/.local
                pip install --user -r requirements.txt
                '''
    }
        }
        stage('Test') {
            steps {
                echo "Testing..."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver...'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
    post {
        always {
            echo "Cleaning up..."
            script {
                env.PATH = "${WORKSPACE}/myapp/.local/bin:${env.PATH}"
            }
        }
    }
}