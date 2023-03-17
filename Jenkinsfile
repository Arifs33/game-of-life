pipeline {

          agent {
		  
		      label {
			  
			      label "slave"
				  customWorkspace "/mnt/slave/workspace/"
			  }
		  }
		  
		  stages {
		  
		     stage ("deploy game-of-") {
			 
			     steps {
				
				 sh "sudo rm -rf /root/.m2/repository"
				 sh "sudo mvn clean install"
				 sh "sudo docker run -itdp 8087:8080 -v /mnt/slave/workspace/gameoflife-web/target:/usr/local/tomcat/webapps --name gameoflife tomcat:9.0.73" 
				 
			
				 }
			 
			 
			 }
		  
		  
		  }
		  
}
