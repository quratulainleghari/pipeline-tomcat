pipeline {
    agent any
    tools {
        maven 'maven'
        jdk '1.8'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                git "https://github.com/sivajavatechie/JenkinsWar.git"
               sh 'mvn clean package'
            }
            post {
                success {
                    archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
                    junit '**/target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
