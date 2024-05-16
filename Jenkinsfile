pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
			echo 'Building'	
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
                        echo 'Pushing'
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
