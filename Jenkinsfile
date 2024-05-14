pipeline {
 agent any
 
 environment {
 FLASK_APP = 'app.py'
 FLASK_ENV = 'development'
 }
 
 stages {
 stage('Build') {
 steps {
 script {
 echo 'Building Python Flask app...'
 sh 'pip install -r requirements.txt'
 }
 }
 }
 stage('Test') {
 steps {
 script {
 echo 'Running tests...'
 // Add any test commands here if needed
 }
 }
 }
 stage('Approval') {
 steps {
 timeout(time: 24, unit: 'HOURS') {
 input message: 'Do you approve the deployment?', submitter: 'admin'
 }
 }
 }
 stage('Deploy') {
 steps {
 script {
 echo 'Deploying Python Flask app...'
 sh 'python app.py &'
 }
 }
 }
 }
 
 post {
 success {
 echo 'Pipeline succeeded!'
 }
 failure {
 echo 'Pipeline failed!'
 }
 }
}
