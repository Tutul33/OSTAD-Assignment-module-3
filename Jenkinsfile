// pipeline {
//     agent any

//     stages {
//         stage('Clone') {
//             steps {
//                 // Checkout source code
//                 git branch: 'main', 
//                 credentialsId: 'github-ssh-key',
//                 url: 'git@github.com:Tutul33/OSTAD-Assignment-module-3.git'
//             }
//         }

//         stage('Install') {
//             steps {
//                 echo 'Installing dependencies...'
//                 sh 'npm install'
//             }
//         }

//         stage('Test') {
//             steps {
//                 echo 'Running tests...'
//                 // Update the script if the test tool supports JUnit XML reporting
//                 sh 'npm run check || exit 1'
//             }
//         }
        
//     }

    
// }

pipeline {
    agent {
        docker {
            image 'node:18'
            args '-u root' // Optional if you need root for permissions
        }
    }

    stages {
        stage('Clone') {
            steps {
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
                sh 'npm run check || exit 1'
            }
        }
    }
}
