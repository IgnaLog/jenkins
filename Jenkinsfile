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
                    // Activar el entorno virtual
                    sh 'cd myapp'
                    sh 'source myapp/venv/bin/activate'
                    // Ir al directorio de la aplicación
                    sh 'cd myapp'
                    // Listar archivos (para depuración)
                    sh 'ls'
                    // Ejecutar el script hello.py
                    sh 'python3 myapp/hello.py'
                    sh 'python3 myapp/hello.py --name=Brad'
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