node{
   
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
   
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Deploy to Tomcat'){
      
      sshagent(['tomcat-dev']) {
        sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@34.206.54.129:/opt/tomcat/apache-tomcat-8.5.37/webapps/'
      }
   }
   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      Qurat''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'qurat@royalcyber.com'
   }
  

}
