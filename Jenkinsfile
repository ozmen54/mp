pipeline {
     environment {
        PATH = "/mnt/c/Software/apache-maven-3.6.3/bin:${env.PATH}"
    }
    agent any
    stages {
        stage('Control Maven and Java versions'){
            steps{
                sh 'mvn -v'
                sh 'java -version'
            }
        }
    post {
        success {
            echo "job is done"
       }
   }
}