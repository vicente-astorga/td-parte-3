pipeline {
    agent any

    stages {
        stage('Clonar repositorio') {
            steps {
                git 'https://github.com/vicente-astorga/td-parte-3.git'
            }
        }

        stage('Construir imagen Docker') {
            steps {
                script {
                    dockerImage = docker.build("react-api")
                }
            }
        }

        stage('Pruebas') {
            steps {
                sh 'npm test'
            }
        }

        stage('Desplegar') {
            steps {
                script {
                    dockerImage.run("-p 80:80")
                }
            }
        }
    }
}
