
pipeline {
   agent any

   tools {
     maven 'Maven3'
   }

   environment {
      DEV_TOMCAT = 'http://dev-server:8080'
      TEST_TOMCAT = 'http://test-server:8080'
      PREPROD_TOMCAT = 'http://preprod-server:8080'
      PROD_TOMCAT = 'http://prod-server:8080'
   }

 stages{
   stage('Get code') {
     steps {
      git 'https://github.com/vicky2399/train-reservation.git'
     }
   }

   stage('Build') {
     steps {
      sh 'mvn clean package'
     }
   }
   
   stage('Deploy to DEV') {
     when { branch 'master' }
     steps {
      echo 'Deploying to DEV environment...'
      sh 'curl -u ${TOMCAT_USER}:${TOMCAT_PASSWORD} --upload-file target/TrainBook-1.0.0-SNAPSHOT.war ${DEV_TOMCAT}/manager/text/deploy?path=/train-reservation&update=true'
     }
   }
   
   stage('Deploy to TEST') {
     when { branch 'master' }
     steps {
      echo 'Deploying to TEST environment...'
      sh 'curl -u ${TOMCAT_USER}:${TOMCAT_PASSWORD} --upload-file target/TrainBook-1.0.0-SNAPSHOT.war ${TEST_TOMCAT}/manager/text/deploy?path=/train-reservation&update=true'
     }
   }
   
   stage('Deploy to PREPROD') {
     when { branch 'master' }
     steps {
      echo 'Deploying to PREPROD environment...'
      sh 'curl -u ${TOMCAT_USER}:${TOMCAT_PASSWORD} --upload-file target/TrainBook-1.0.0-SNAPSHOT.war ${PREPROD_TOMCAT}/manager/text/deploy?path=/train-reservation&update=true'
     }
   }
   
   stage('Deploy to PROD') {
     when { branch 'master' }
     steps {
      echo 'Deploying to PROD environment...'
      input message: 'Approve deployment to PROD?', ok: 'Deploy'
      sh 'curl -u ${TOMCAT_USER}:${TOMCAT_PASSWORD} --upload-file target/TrainBook-1.0.0-SNAPSHOT.war ${PROD_TOMCAT}/manager/text/deploy?path=/train-reservation&update=true'
     }
   }
 }
}
