pipeline {
   agent any

   tools {
     maven 'maven3'
   }

   stages('Get code') {
     steps {
      git 'https://github.com/vicky2399/train-reservation.git'
     }
   }

   stages('build') {
     steps {
     sh 'mvn clean package'
     }
    }
}
