pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /home/jenkinsbuild/.m2:/var/maven/.m2 -e MAVEN_CONFIG=/var/maven/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                //sh 'mvn -B -DskipTests clean package'
                //sh 'mvn help:evaluate -Dexpression=settings.localRepository'
                sh 'ls'
                sh 'printenv'
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
