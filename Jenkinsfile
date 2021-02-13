pipeline
{
	agent any 
	environment{
		PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin" 
	}
	
	stages{
		stage('SCM Checkout'){
			steps{
				git credentialsId: 'github', url: 'https://github.com/saleemnmalik/6pmwebapp'
				 }
			
		
			}
		stage('MVN Build'){
			steps{
					
						
						sh "mvn clean package"
					
			}		
			
		
		}

        stage('Deploy Dev'){
			steps{
					
						
						sshagent(['tomcat-dev']) {
                                    //stop tomcat
                                    sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.32.111 /opt/tomcat8/bin/shutdown.sh"
                                   //copy war file to Tomcat
                                   sh "scp target/6pmwebapp.war ec2-user@172.31.32.111:/opt/tomcat8/webapps/"
                                   //start tomcat 
                                   sh "ssh ec2-user@172.31.32.111 /opt/tomcat8/bin/startup.sh"
                    }
					
			}		
			
		
		}
		
	
	}
	
post {
  success {
   echo "email"
  }
}


}
