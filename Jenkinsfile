pipeline {
   agent any

   tools {
     maven 'Maven3'
   }

 stages{
   stage('Get code') {
     steps {
      git 'https://github.com/vicky2399/train-reservation.git'
     }
   }


   stage('build') {
     steps {
     sh 'mvn clean package'
     }
    }
 }
}
