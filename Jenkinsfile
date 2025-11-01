pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'MAVEN_HOME'
    }
	// environment{
	// 	MAVEN_HOME=tool'MAVENHOME'
	// 	PATH="${env.MAVEN_HOME}/bin:${env.PATH}"
	// }
    stages {
        stage('Checkout') {
			steps{
            git branch: 'Jenkins01', url: 'https://github.com/gkmanivannan88-sketch/Jenkins-Pipeline.git'
        
				}
		}
        stage('Build') {
			steps{
            bat 'mvn clean install'
			}
        }
   //      stage('Run Application') {
			// steps{
				
   //         			 bat 'mvn test'
			// }
   //      }
        stage('Test') {
            // write your logic here
			steps{
				
           			 bat  'mvn test'
			}
            post {
                success {
                    junit 'target/surefire-reports/*.xml'
					echo 'Build and Tests Passed Successfully'
                }
				failure {
                    junit 'target/surefire-reports/*.xml'
					echo 'Build and Tests failed'
                }
            }
        }
    }
}




