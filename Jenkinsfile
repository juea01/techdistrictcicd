pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
			./jenkins/build/mvn.sh mvn -B -DskipTests clean package	
               '''
            }
        }
        stage('Test') {
            steps {
                ./jenkins/test/mvn.sh mvn test
            }
        }
	stage('Push') {
        	steps {
		 sh '''
                        ./jenkins/push/push.sh
                   '''
		}
        }
        stage('Deploy') {
			 steps {
                sh '''
                        echo 'Running Deployscript on remote machine'
                        ssh -i "/var/jenkins_home/prod/techDistrictWebServerKeyPair.pem" prod-user@ec2-54-206-69-220.ap-southeast-2.compute.amazonaws.com /home/prod-user/deployscript/deploy.sh
                '''
            }
        }
    }
}
