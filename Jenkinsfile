pipeline{
 agent {
      docker {
 label 'docker-node'
 image 'maven'
 args '-v /tmp:/tmp -p 80:80'
 }
 }
 environment {
 GIT_COMMITTER_NAME = 'jenkins'
 }
 options {
 timeout(time: 6, unit: 'HOURS')
 }
 stages {
 stage('Build') {
 steps {
    echo scm.getUserRemoteConfigs()

     sh 'mvn clean install'
 }
 }
 stage('Archive') {
 when {
 branch '*/master'
 }
 steps {
 archive '*/target/**/*'
 junit '*/target/surefire-reports/*.xml'
 }
 }
 }
 post {
 always {
 deleteDir()
 }
 }
    
}

 
