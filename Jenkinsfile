pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout source code
                git branch: 'main', 
                credentialsId: 'github-ssh-key',
                url: 'git@github.com:Tutul33/OSTAD-Assignment-module-3.git'
            }
        }

        stage('Read hello.txt') {
            steps {
                script {
                    echo "Contents of Hello"
                }
            }
        }
    }

    
}