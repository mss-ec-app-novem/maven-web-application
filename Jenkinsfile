node("master") 
{
    
  def mavenHOME = tool name: "maven3.8.4"    
stage('CheckoutCode')
{ 
git branch: 'development', credentialsId: '8b54a450-5718-4319-9fab-610112012730', url: 'https://github.com/mss-ec-app-novem/maven-web-application.git'
}
stage('build')
{

  sh "${mavenHOME}/bin/mvn clean package"
}
}    
