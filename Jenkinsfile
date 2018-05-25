podTemplate(label: 'kubernetes',
  containers: [
    containerTemplate(name: 'maven', image: 'maven:3.5.2-jdk-8-alpine', ttyEnabled: true, command: 'cat')
  ]) {
    node("kubernetes"){
        container("maven") {
           stage('Preparation') { // for display purposes
              git 'https://github.com/jglick/simple-maven-project-with-tests.git';
           }
           stage('Build') {
              sh "mvn -Dmaven.test.failure.ignore clean package"
           }
           stage('Unit Test') {
              junit '**/target/surefire-reports/TEST-*.xml'
           }
           stage('Archive') {
              archive 'target/*.jar'
           }
           stage('Upload to Artifactory') {
              echo "steps to upload to artifactory goes here"
           }     
           stage('Deploy to Dev') {
              echo "Steps to deploy to Development"
           } 
           stage('Functional tests') {
              echo "Steps to execute functional tests"
           }
           stage('Complaince tests') {
              echo "Steps to execute functional tests"
           } 
           stage('Promote to higher environment') {
              echo "promote to next environment"
           }
        }
    }
}
