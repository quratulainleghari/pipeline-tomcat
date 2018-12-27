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

       
      
      stage ('Compile-Package') {
            steps {
                git "https://github.com/javahometech/my-app"
              sh 'mvn clean package'
            }
      }
  
   stage('Deploy to Tomcat'){
      steps {
      
      //sshagent(['tomcat-dev']) {
        //sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@34.206.54.129:/opt/tomcat/apache-tomcat-8.5.37/webapps/'
       
         sh 'sudo cp /home/jenkins/workspace/pipeline-tomcat/target/*.war /opt/tomcat/apache-tomcat-8.5.37/webapps/'
        // sh 'sudo rm -rf ROOT.war'
         //sh 'sleep 30'
        //sh 'sudo mv /opt/tomcat/apache-tomcat-8.5.37/webapps/*.war /opt/tomcat/apache-tomcat-8.5.37/webapps/ROOT.war'
     // }
   }
   }
  
       stage ('Email Notification'){
          steps{
      emailext (
    subject: "Job '${env.JOB_NAME} ${env.BUILD_NUMBER}'",
    body: """<p>Check console output at <a href="${env.BUILD_URL}">${env.JOB_NAME}</a></p>""",
    to: "qurat@royalcyber.com",
    from: "leghari.quratulain@gmail.com"
)
          }
       }
      }
   }


