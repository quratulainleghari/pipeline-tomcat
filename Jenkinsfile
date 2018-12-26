pipeline {
   agent {label "tomcat"}
    
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

       
      
      stage ('SCM Checkout') {
            steps {
                git "https://github.com/javahometech/my-app"
              //sh 'mvn clean package'
            }
      }
  // stage('SCM Checkout'){
     // steps {
     //git 'https://github.com/javahometech/my-app'
  // }
  // }
   stage('Compile-Package'){
      // Get maven home path
      steps {
     // def mvnHome =  tool name: 'maven', type: 'maven'   
      //sh "${mvnHome}/bin/mvn package"
         sh 'mvn clean package'
   }
   }
   stage('Deploy to Tomcat'){
      steps {
      
      //sshagent(['tomcat-dev']) {
        //sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@34.206.54.129:/opt/tomcat/apache-tomcat-8.5.37/webapps/'
       
         sh 'sudo cp /home/jenkins/workspace/pipeline-tomcat/target/*.war /opt/tomcat/apache-tomcat-8.5.37/webapps/'
       
     // }
   }
   }
   //stage('Email Notification'){
     // steps {
      //mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      //Thanks
      //Qurat''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'qurat@royalcyber.com'
   //}
   //}
      }
   }


