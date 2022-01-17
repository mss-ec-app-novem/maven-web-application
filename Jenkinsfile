node("master") 
{
// Default values
  def colorName = 'RED'
  def colorCode = '#FF0000'
  def subject = "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
  def summary = "${subject} (${env.BUILD_URL})"

  // Override default values based on build status
  if (buildStatus == 'STARTED') {
    color = 'YELLOW'
    colorCode = '#FFFF00'
  } else if (buildStatus == 'SUCCESSFUL') {
    color = 'GREEN'
    colorCode = '#00FF00'
  } else {
    color = 'RED'
    colorCode = '#FF0000'
  }
    
  // Send notifications
  slackSend (color: colorCode, message: summary)
}
  def mavenHOME = tool name: "maven3.8.4"    
stage('CheckoutCode')
{ 
git branch: 'development', credentialsId: '8b54a450-5718-4319-9fab-610112012730', url: 'https://github.com/mss-ec-app-novem/maven-web-application.git'
}
stage('build')
{
/*
  sh "${mavenHOME}/bin/mvn clean package"
}
stage('ExecuteSonarQubeReport')
{
sh " ${mavenHOME}/bin/mvn clean sonar:sonar"
}
stage('uploadArtifactIntoNexus')
{
sh "${mavenHOME}/bin/mvn clean deploy"
}

stage("DeployAppIntoTomcat")
{
sshagent(['7eef2cf2-37cf-46e0-b6a6-2f77ff129df9']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.109.214.10:/opt/apache-tomcat-9.0.56/webapps/"
}
*/
}
stage('SendNotifications'){
emailext body: '''Build over...

Regards,
A Ishahak.
9505728116.''', subject: 'Build over', to: 'aishahak1997@gmail.com'
}
}    
