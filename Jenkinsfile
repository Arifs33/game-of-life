pipeline {
	agent {
		node {
			label " built-in"
			customWorkspace "/mnt/project"
		}
	}
	
	stages {
		stage ('clone repo') {
			steps {
			    sh " sudo rm -rf game-of-life*"
				sh " sudo git clone https://github.com/Arifs33/game-of-life.git"
			}
		}
		
		stage ('create build') {
			steps {
			dir ('/mnt/project/game-of-life') {
			    
			    sh " sudo mvn clean install"
			
			}
			}
		}
		stage ('copy on slave') {
			steps {
					sh "sudo chmod -R 777 /mnt/project/game-of-life/gameoflife-web/target/gameoflife.war"
					sh "sudo scp -i linserver.pem /mnt/project/game-of-life/gameoflife-web/target/gameoflife.war ec2-user@43.205.115.22:/mnt"
					sh "sudo scp -i linserver.pem /mnt/project/game-of-life/gameoflife-web/target/gameoflife.war ec2-user@13.232.231.133:/mnt"
		}
		}
		
		stage ('copy app slave-1'){
			agent {
		node {
			label "qa"
			customWorkspace "/mnt"
		}
	}
			steps {
				sh "sudo cp gameoflife.war /mnt/compose/file-1"
				
				
			
			}
		}
		
		stage ('deploy app using docker compose slave-1'){
			agent {
		node {
			label "qa"
			customWorkspace "/mnt/compose"
		}
	}
			steps {
				sh "sudo docker-compose up -d"
				
			
			}
		}
		
		
		stage ('copy app slave-2'){
			agent {
		node {
			label "dev"
			customWorkspace "/mnt"
		}
	}
			steps {
				sh "sudo cp gameoflife.war /mnt/compose/file-1"
				
				
			
			}
		}
		stage ('deploy app using docker compose slave-2'){
			agent {
		node {
			label "dev"
			customWorkspace "/mnt/compose"
		}
	}
			steps {
				sh "sudo docker-compose up -d"
				
				
			
			}
		}
	}
}
