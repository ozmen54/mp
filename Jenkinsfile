pipeline {
   agent any

   environment {
       PATH="/mnt/c/Software/apache-maven-3.6.3/bin:${env.PATH}"
       registry = "aozmen54/webapp"
       registryCredentials = 'DHub-1'
       dockerImage = ''
   }

   stages {
       stage('Maven and Java versions') {
           steps {
               sh 'mvn -v'
               sh 'java -version'
           }
       }

       stage('Checkout mp project from GitHub') {
           steps {
               git 'https://github.com/ozmen54/mp.git'
           }
       }

       stage('Build jar file') {
           steps {
               sh 'mvn clean package'
           }
       }
       stage('Bild docker image') {
           steps {
               script {
                   dockerImage = docker.build registry
               }
           }
       }

       stage('Push the docker image to the hub'){
           steps {
               script {
                   docker.withRegistry('', registryCredentials){
                       dockerImage.push()
                   }
               }
           }
       }
   }
   post {
       success {
           echo 'Everything is fine.'
       }
   }
}