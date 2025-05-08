pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                // Checkout source code
                git branch: 'main', 
                credentialsId: 'github-ssh-key',
                url: 'git@github.com:Tutul33/OSTAD-Assignment-module-3.git'
            }
        }

        stage('Install') {
            steps {
                echo 'Installing dependencies...'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Update the script if the test tool supports JUnit XML reporting
                //sh 'npm run check || exit 1'
                sh 'npx jest --ci --reporters=default --reporters=jest-junit || exit 1'
            }
        }

        stage('Report') {
           steps {
             echo 'Publishing test results...'
             junit 'test-results/results.xml'
           }
       }
    }

    
}