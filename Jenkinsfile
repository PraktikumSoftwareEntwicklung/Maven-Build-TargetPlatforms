pipeline {
    agent {
        docker {
            image 'custom_maven:latest'
            args '-v /home/jenkinsbuild/.m2:/var/maven/'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mkdir $PWD/?/'
                sh 'mkdir $PWD/?/.m2/'
                sh 'cp -r /var/maven/* $PWD/?/.m2/'
                sh 'mvn -B -DskipTests clean package'
                sh 'cp -r $PWD/?/.m2/* /var/maven/'
                sh 'printenv'
                sh 'mvn help:evaluate -Dexpression=settings.localRepository'
		sh 'ls'
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
