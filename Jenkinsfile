pipeline {
    agent { label 'dolvera-node'}

    options {
        skipDefaultCheckout(true)
    }

    environment {
        REPO_URL = 'https://github.com/OLV3RAG/ansible-jenkins.git'
        BRANCH = 'develop'
    }

       stages {

        stage('Limpiar workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Checkout manual') {
            steps {
                sh '''
                echo "Clonando repo..."
                git clone --branch $BRANCH --single-branch $REPO_URL .
                '''
            }
        }

        stage('Verificar repo') {
            steps {
                sh '''
                echo "Usuario:"
                whoami

                echo "Rama:"
                git branch

                echo "Archivos:"
                ls -la
                '''
            }
        }

        stage('Instalar Ansible') {
            steps {
                sh '''
                if ! command -v ansible-playbook >/dev/null 2>&1; then
                    echo "Instalando Ansible..."
                    sudo apt update
                    sudo apt install -y ansible
                else
                    echo "Ansible ya está instalado"
                fi
                '''
            }
        }

        stage('Debug Ansible') {
            steps {
                sh '''
                echo "Ruta de Ansible:"
                which ansible-playbook || echo "No encontrado"

                echo "Versión:"
                ansible-playbook --version || echo "Error"
                '''
            }
        }

        stage('Ejecutar Ansible') {
            steps {
                sh '''
                echo "Ejecutando playbook..."
                ansible-playbook playbook.yml
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente'
        }
        failure {
            echo 'Pipeline falló'
        }
    }
}