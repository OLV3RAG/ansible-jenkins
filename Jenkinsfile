pipeline {
    agent { label 'dolvera-node' }

    options {
        skipDefaultCheckout(true) 
    }

    environment {
        REPO_URL = 'https://github.com/OLV3RAG/ansible-jenkins.git'
        BRANCH = 'develop'
    }

    stages {

        stage('Checkout manual') {
            steps {
                sh '''
                echo "Clonando repo..."
                rm -rf *
                git clone --branch $BRANCH --single-branch $REPO_URL .
                '''
            }
        }

        stage('Verificar') {
            steps {
                sh '''
                echo "Usuario:"
                whoami

                echo "Rama actual:"
                git branch

                echo "Contenido:"
                ls -la
                '''
            }
        }
    }
}