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
        stage('Ejecutar Ansible') {
    steps {
        sh '''
        echo "Ejecutando playbook..."
        ansible-playbook playbook.yml
        '''
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

        stage('Verificar') {
            steps {
                sh '''
                echo "Usuario:"
                whoami

                echo "Rama:"
                git branch

                echo "Contenido:"
                ls -la
                '''
            }
        }
    }
}