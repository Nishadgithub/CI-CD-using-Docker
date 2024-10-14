pipeline {
    agent any
	
 environment{
        PATH = "/opt/apache-maven-3.9.9/bin:$PATH"
 }
	 
 stages {
      stage('checkout') {
           steps {
             
                git credentialsId: 'Nishad', url: 'https://github.com/Nishadgithub/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn  clean package'             
          }
        }   
 stage("Deploy"){
            steps{
                    sshagent(['SSH_Tomcat']) {
                                        
                        sh """
                            scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/example-tomcat-war/target/SimpleTomcatWebApp.war ec2-user@172.31.45.90:/opt/tomcat9/webapps/
                    
                            ssh ec2-user@172.31.45.90 /opt/tomcat9/bin/shutdown.sh
                    
                            ssh ec2-user@172.31.45.90 /opt/tomcat9/bin/startup.sh
                
                """
                }
            }
      }
    }
	}
    
