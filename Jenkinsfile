pipeline {
  agent any
  tools {
    maven 'maven'
  }
//   environment {
    //    TOMCAT_SERVER = 'tomcat_key' // Your configured SSH credential ID
//    }
  stages {
//    stage ('Initialize') {
//             steps {
//                 sh '''
//                     M2_HOME=/opt/maven
//                     M2=/opt/maven/bin
//                     PATH=$PATH:$HOME/bin/:$JAVA_HOME:$M2:$M2_HOME
//                     export PATH
//                     echo "PATH = ${PATH}"
//                     echo "M2_HOME = ${M2_HOME}"
//                     whoami
//                 '''
//             }
//         }
    stage('Build app') {
      steps {
        sh 'mvn clean install package'
      }
    }
  //  stage('Push Artifact to S3') {
  //    steps {
  //      sh 'aws s3 cp webapp/target/webapp.war s3://demo-test198'
//      }
//}
    
    stage('Deploy to tomcat') {
      steps {
        // withCredentials([sshUserPrivateKey(credentialsId: TOMCAT_SERVER, keyFileVariable: 'SSH_KEY')]) {
         sh 'scp  -i /var/lib/jenkins/demo.pem -o "StrictHostKeyChecking=no" /var/lib/jenkins/workspace/demo/webapp/target/webapp.war ubuntu@3.110.166.71:/opt/tomcat/webapps'
//           sh 'sudo ansible-playbook deploy-new.yml'
    //  }
    }
    }
//     stage('building docker image from docker file by tagging') {
//       steps {
//         sh 'docker build -t phanirudra9/phani9-devops:$BUILD_NUMBER .'
//       }   
//     }
//     stage('logging into docker hub') {
//       steps {
//         sh 'docker login --username="phanirudra9" --password="9eb876d4@A"'
//       }   
//     }
//     stage('pushing docker image to the docker hub with build number') {
//       steps {
//         sh 'docker push phanirudra9/phani9-devops:$BUILD_NUMBER'
//       }   
//     }
//     stage('deploying the docker image into EC2 instance and run the container') {
//       steps {
//         sh 'ansible-playbook deploy.yml --extra-vars="buildNumber=$BUILD_NUMBER"'
//       }   
//     }  
}
// post {
//      always {
//        emailext to: 'nammimahesh01@gmail.com',
//        attachLog: true, body: "Dear team pipeline is ${currentBuild.result} please check ${BUILD_URL} or PFA build log", compressLog: false,
//        subject: "Jenkins Build Notification: ${JOB_NAME}-Build# ${BUILD_NUMBER} ${currentBuild.result}"
//     }
// }
}
