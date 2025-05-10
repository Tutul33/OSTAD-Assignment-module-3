pipeline {
    agent any

    environment {
        NODE_HOME = tool name: 'NodeJS 18', type: 'NodeJSInstallation'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Clone Repo') {
            steps {
                git credentialsId: 'github-ssh-key', url: 'git@github.com:Tutul33/OSTAD-Assignment-module-3.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Make sure you're installing dependencies here
                sh 'npm install'  // This will install jest, jest-junit, and any other dependencies
            }
        }

        stage('Run Tests') {
            steps {
                // Running the tests, with results outputting to JUnit-compatible format
                sh 'npm test'
            }
            post {
                always {
                    junit '**/test-reports/junit.xml'  // Path to the JUnit report
                }
            }
        }
    }

    post {
        success {
            //discordSend description: "✅ Build Success", webhookURL: "${DISCORD_WEBHOOK}"
            echo 'Build Success';
        }
        failure {
            //discordSend description: "❌ Build Failed", webhookURL: "${DISCORD_WEBHOOK}"
            echo 'Build failed';
        }
    }
}
