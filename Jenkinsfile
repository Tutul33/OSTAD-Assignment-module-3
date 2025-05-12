pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git credentialsId: 'github-ssh-key', url: 'git@github.com:Tutul33/OSTAD-Assignment-module-3.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies..........'
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mkdir -p test-results && npm test -- --reporter-options mochaFile=./test-results/results.xml'
            }
        }

        stage('Publish Test Results') {
            steps {
                junit '**/test-results/*.xml'
            }
        }

        stage('Notify Discord') {
            steps {
                script {
                         def now = new Date().format("yyyy-MM-dd HH:mm:ss", TimeZone.getTimeZone('UTC'))
                         def message = "Build Status: ${currentBuild.currentResult} at ${now} UTC from Jenkins Server Build."
                         def discordWebhookUrl = 'https://discord.com/api/webhooks/1370351297957597215/IvDHPwvUF9CSEwx3jbtMBhMiLvfKed--1CLP31y8XDYXQP2MHAvoVdliFjijw_3EU2i6'
             
                         sh """
                             curl -X POST -H "Content-Type: application/json" \
                             -d '{"content": "${message}"}' \
                             ${discordWebhookUrl}
                         """
                       }
            }
        }
    }
}
