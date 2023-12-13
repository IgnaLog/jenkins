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
                python3 -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                cat requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing..."
                script {
                    // Activate the virtual environment
                    sh 'cd myapp'
                    sh 'python3 -m venv venv'
                    sh '. venv/bin/activate' // Use a dot to source the activate script
                    
                    // Install dependencies (including the fire module)
                    sh 'pip install -r requirements.txt'
                    
                    // Display the current Python environment
                    sh 'which python'
                    sh 'python --version'
                    
                    // Execute your test script
                    sh 'python myapp/hello.py'
                }
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
}