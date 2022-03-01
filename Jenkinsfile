pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('a11b6fef-7f02-4bf1-916f-c7a61b208540')
	}

	stages {

		stage('Build') {

			steps {
				sh """
	    	docker build -t npatil15/pythondemo15:latest .
                 docker ps -a
		 """
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
			   sh """
        docker push npatil15/pythondemo15:latest
        
        """
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
