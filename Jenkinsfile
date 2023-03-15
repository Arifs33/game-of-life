pipeline {

          agent {
		  
		      label {
			  
			      label "built-in"
				  customWorkspace "/mnt/project3/"
			  }
		  }
		  
		  stages {
		  
		     stage ("deploy game-of-") {
			 
			     steps {
				 
				 sh "sudo rm -rf /root/.m2/repository"
				 sh "sudo mvn clean install"
				 sh "sudo docker run -itdp 8087:8080 -v /mnt/project3/gameoflife-web/target:/usr/local/tomcat/webapps --name gameoflife tomcat:9.0.73"
				 
			
				 }
			 
			 
			 }
		  
		  
		  }
		  
}
