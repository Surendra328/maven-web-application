## Groovy

node
{

def mavenHome = tool name: "Maven 3.6.3"
 stage('CheckoutCode')
 
 {
  git branch: 'development', credentialsId: 'f4f64e23-7f4e-4278-97f8-5e7c5b2a72c2', url: 'https://github.com/Surendra328/maven-web-application.git'
 }

 stage('Build')
 {
  sh "${mavenHome}/bin/mvn clean package"
  }
 \*stage('Execute sonarqube report')
 {
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 stage('upload artifact into nexus')
 {
 sh "${mavenHome}/bin/mvn clean deploy"
 }
 stage('Deploy Application into Tomcat server')
 {

     sshagent(['44f6b722-b2d8-4724-838c-198788796328']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.9.170:/opt/apache-tomcat-8.5.70/webapps"
}
  
 }*/
 stage('Send email notification')
 {
 mail bcc: '', body: 'Build over', cc: '', from: '', replyTo: '', subject: 'Build over', to: 'galisaisurendra2511@gmail.com'
 }
}
