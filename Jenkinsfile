pipeline {
        agent {
        label 'dolvera-node'
    }
    stages {
        stage('Step 1 - Detect OS') {
            steps {
                script {
                    if (isUnix()) {
                        echo "El nodo está corriendo en Linux/Unix"
                    } else {
                        echo "El nodo está corriendo en Windows"
                    }
                }
            }
        }

        stage('Step 2 - Mostrar usuario (whoami)') {
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

        stage('Step 3 - Info adicional') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'uname -a'
                    } else {
                        bat 'ver'
                    }
                }
            }
        }
    }
}