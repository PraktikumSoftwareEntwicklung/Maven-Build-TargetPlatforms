pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package'
		sh 'mvn --global-settings "/home/jenkinsbuild/settings.xml" help:evaluate -Dexpression=settings.localRepository'
            }
        }
	stage('Test') {
            steps {
                sh 'mvn test' 
            }
            /*post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }*/
	}
    }
}
