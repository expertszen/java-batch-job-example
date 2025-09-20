pipeline {
    agent any
    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }
    stages {
        stage('Checkout') {
            steps {
                // write your logic here
            }
        }
        stage('Build') {
            // write your logic here
            echo 'Building...'
        }
        stage('Run Application') {
            // write your logic here
        }
        stage('Test') {
            // write your logic here
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Post Build Notification') {
            // write your logic here
            steps{
                script{
                    withCredentials([usernamePassword(crendentialsId: 'gmail-smtp',
                                                    usernameVariable: 'SMTP_USER',
                                                      passwordVariable: 'SMTP_PASS')]){
                        emailext(
                            subject: "Jenkins Build Notification: $(currentBuild.fullDisplayName}",
                            body:"""
                                <h3> Build Completed <h3>
                                <p> Job: ${env.JOB_NAME}</p?
                                <p>Build Number: ${env.BUILD_NUMBER}</p?
                                <p>Status: ${currentBuild.currentResult}</p>
                                """,
                            to "lead.engineer@example.com",
                            from : ${SMTP_USER}",
                            replyTo: "${SMTP_USER}",
                            mimeType:'text/html',
                            attachLog:true,
                            smtpHost: 'smtp.gmailcom',
                            smtpPort:587,
                            useSsl:false,
                            useTls: true,
                            smtpUsername: "${SMTP_USER}",
                            smtpPassword:"${SMTP_PASS}")}
            
    }
    }
}
