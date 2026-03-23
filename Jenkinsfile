pipeline {
    agent any

    options {
        skipDefaultCheckout(true) // 🔥 ESTO SOLUCIONA TU ERROR
    }

    stages {

        stage('Checkout manual') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'git clone https://github.com/OLV3RAG/ansible-jenkins.git .'
                    } else {
                        bat 'git clone https://github.com/OLV3RAG/ansible-jenkins.git .'
                    }
                }
            }
        }  

        stage('Whoami') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'whoami'
                    } else {
                        bat 'whoami'
                    }
                }
            }
        }

        stage('Test Git') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'git --version'
                    } else {
                        bat 'git --version'
                    }
                }
            }
        }
    }
}