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
                sh 'ls $PWD/'
                sh 'mkdir $PWD/test/'
                sh 'ls $PWD/test/'
                sh 'ls $PWD/?/.m2/'
                sh 'cp -r $PWD/?/.m2/* $PWD/test/'
                sh 'ls $PWD/test/'
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
