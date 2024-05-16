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
