pipeline {
    agent {
        docker {
            image 'custom_maven:latest' 
            args '-v /home/jenkinsbuild/.m2:/var/maven2/' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package'
                //sh 'mvn help:evaluate -Dexpression=settings.localRepository'
                sh 'ls -ld $PWD'
                sh 'ls -ld /var/maven/'
                sh 'ls -ld /var/maven2/'
                sh 'ls /var/'
                sh 'ls /var/maven/'
                sh 'ls $PWD/?/.m2/'
                sh 'cp -r $PWD/?/.m2/* /var/maven/'
                sh 'ls /var/maven/'
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
