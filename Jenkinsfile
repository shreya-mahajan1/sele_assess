pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git https://github.com/shreya-mahajan1/sele_assess.git
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Run Selenium Tests') {
            steps {
                sh 'pytest --html=report.html --self-contained-html'
            }
        }
        stage('Publish Report') {
            steps {
                publishHTML(target: [
                    reportName: 'Test Report',
                    reportDir: '.',
                    reportFiles: 'report.html'
                ])
            }
        }
    }
}