pipeline{
 agent any
 environment {
 GIT_COMMITTER_NAME = 'jenkins'
 }
 options {
 timeout(time: 6, unit: 'HOURS')
 }
 stages {
 stage('Build') {
 steps {
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

 
