node("master") 
{
    
  def mavenHOME = tool name: "maven3.8.4"    

 try{   
  SendSlackNotification("STARTED")
 stage('CheckoutCode')
{ 
git branch: 'development', credentialsId: '8b54a450-5718-4319-9fab-610112012730', url: 'https://github.com/mss-ec-app-novem/maven-web-application.git'
}
 stage('build'){
sh "${mavenHOME}/bin/mvn clean package"
}
}    
catch(e){
  // If there was an exception thrown, the build failed
    currentBuild.result = "FAILED"
    throw e
     }
finally {
    // Success or failure, always send notifications
    notifyBuild(currentBuild.result)
     }
}
def SendSlackNotification(String buildStatus = 'STARTED') {
  // build status of null means successful
  buildStatus =  buildStatus ?: 'SUCCESSFUL'

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
