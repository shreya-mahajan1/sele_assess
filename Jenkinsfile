pipeline {
    agent any 

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/shreya-mahajan1/sele_assess.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }
        stage('Run Selenium Test') {
            steps {
                bat 'pytest sele.py'
            }
        }
        stage('Archive Test Report') {
            steps {
                archiveArtifacts artifacts: 'report.html', fingerprint: true
            }
        }
        stage('Send Email') {
            steps {
                emailext(
                    subject: 'Selenium Test Report',
                    body: 'Test report.',
                    attachmentsPattern: 'report.html',
                    to: 'shreya.mhajn@gmail.com'
                )
            }
        }
    }
}