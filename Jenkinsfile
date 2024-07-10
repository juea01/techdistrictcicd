pipeline {
    agent any

    environment {
        GIT_CREDENTIALS = 'GithubToken' // Replace with the ID of your credentials
    }

    stages {

	stage('Check Out') {
            steps {
		  checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    doGenerateSubmoduleConfigurations: false, 
                    extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'java-app/productlistingapp']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/juea01/shoppingDisProductlis.git',
                        credentialsId: env.GIT_CREDENTIALS
                    ]]
                ])
		}
        }
        stage('Build') {
            steps {
                sh '''
			./jenkins/build/mvn.sh mvn -B -DskipTests clean package	
               '''
            }
        }
        stage('Test') {
            steps {
		sh '''
                       ./jenkins/test/mvn.sh mvn test
                  ''' 
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
                        ssh -i "/var/jenkins_home/prod/techDistrictWebServerKeyPair.pem" ec2-user@ec2-54-206-144-224.ap-southeast-2.compute.amazonaws.com /home/prod-user/deployscript/deploy.sh 
                '''
            }
        }
    }
}
