pipeline {
    agent any

    tools {
        // Must match a configured NodeJS tool installation in "Manage Jenkins -> Tools"
        nodejs 'NodeJS'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // Installs newman globally for the Jenkins workspace agent
                bat '''
                    call npm install -g newman newman-reporter-htmlextra
                '''
            }
        }

        stage('Execute Postman Tests') {
            steps {
                bat '''
                    if not exist "newman" mkdir newman
                    call newman run Booking_API.json -e Environment.json -r cli,htmlextra --reporter-htmlextra-export newman/report.html
                '''
            }
        }
    }

    post {
        always {
            // Publishes the HTML report using the Jenkins HTML Publisher Plugin
            publishHTML([
                allowMissing: false,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'newman',
                reportFiles: 'report.html',
                reportName: 'Newman API Execution Report',
                reportTitles: 'Restful Booker API Test Report'
            ])
        }
    }
}
