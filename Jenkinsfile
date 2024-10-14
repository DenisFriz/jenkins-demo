pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/DenisFriz/jenkins-demo.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    def customImage = docker.build("my-node-app:latest")
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    // Run 'npm install' inside the Docker container
                    customImage.inside {
                        sh 'npm install'
                    }
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Run build steps inside the Docker container
                    customImage.inside {
                        echo 'Building...'
                        // Здесь можно добавить дополнительные команды сборки, если требуется
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests inside the Docker container
                    customImage.inside {
                        echo 'Testing...'
                        // Здесь можно запустить команды для тестирования
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Run deploy steps inside the Docker container (или вне, если нужно)
                    echo 'Deploying...'
                    // В зависимости от вашей логики деплоя, это может быть выполнено внутри или вне контейнера
                }
            }
        }
    }
}
