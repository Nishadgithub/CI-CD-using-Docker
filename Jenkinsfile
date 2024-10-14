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
 
    }
	}
    
