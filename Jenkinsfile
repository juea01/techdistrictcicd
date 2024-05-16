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
                echo 'Testing'
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
			echo 'Deploying'
		'''
            }
        }
    }
}
