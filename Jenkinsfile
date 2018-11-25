pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /home/jenkinsbuild/.m2:/tmp/maven/' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package'
                //sh 'mvn help:evaluate -Dexpression=settings.localRepository'
                sh 'ls /tmp/'
                sh 'mkdir /tmp/maven'
                sh 'ls /tmp/maven'
                sh 'cp -r $PWD/?/.m2/ /tmp/maven/'
                sh 'ls /tmp/maven/.m2/'
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
