pipeline {
	agent { 
		label 'linux-node' 
	}
 
	stages {
		stage('Checkout') { 
			steps { 
				git credentialsId: 'f5e583d6-8782-4be4-a03e-daac44dcafc6', url: 'https://github.com/Kestrel-opswerks/node-webapp.git', branch: 'main' 
			} 
		} 

		stage('Build Docker Image') { 
			steps { 
				script { 
					docker.build('node-webapp:latest') 
				} 
			}
		} 

		stage('Run Docker Container') { 
			steps { 
				script { 
					docker.image('node-webapp:latest').run('-d -p 3000:3000') 
				} 
			} 
		} 
	} 
}
