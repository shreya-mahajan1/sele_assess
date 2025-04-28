pipeline { 
    agent any 
 
    stages { 
        stage('Checkout Code') { 
            steps { 
                git branch: 'main', url: 'https://github.com/ShivRaiGithub/DevopsAssess.git' 
            } 
        } 
        stage('Install Dependencies') { 
            steps { 
                sh 'pip3 install -r requirements.txt' 
            } 
        } 
        stage('Run Selenium Test') { 
            steps { 
                sh 'pytest sele.py' 
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
                    to: 'sshaktirai@gmail.com' 
                ) 
            } 
        } 
    } 
} 