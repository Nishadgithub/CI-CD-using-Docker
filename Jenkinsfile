pipeline {
    agent any
	
 environment{
        PATH = "/opt/apache-maven-3.9.9/bin:$PATH"
 }
	 
 stages {
      stage('checkout') {
           steps {
             
                git credentialsId: 'Password', url: 'https://github.com/Nagesh05021993/hello-world-tomcat-war.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn  clean package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp nikhilnidhi/samplewebapp:latest'
                //sh 'docker tag samplewebapp nikhilnidhi/samplewebapp:$BUILD_NUMBER'
               
          }
        }
     
 
    }
	}
    
