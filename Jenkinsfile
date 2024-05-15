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

 stage('Approve via email') {
 steps {
 emailext to: 'devopsmay24batch@gmail.com', subject: 'New build is waiting for your approval', body: '<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/1999/REC-html401-19991224/strict.dtd"><html><p>A new build has been deployed, please view it by visiting <a href=http://localhost:8000/>"http://localhost:8080/"</a>, please approve this deployment by clicking on <a href=http://localhost:8080/job/demopythonapp/${BUILD_NUMBER}/input/>"http://localhost:8080/"</a></p></html>', attachLog: true
 timeout(time: 60, unit: 'MINUTES') {
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
 sh 'python app.py'
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
