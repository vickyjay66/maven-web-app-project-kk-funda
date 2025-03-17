node 
{
  def mavenHome=tool name: "maven3.9.9"
  stage ('git checkout')
  { 
    git branch: 'devoplment', credentialsId: 'b9f7ff0f-a9b5-4401-b83d-b5ba2e01514e', url: 'https://github.com/vickyjay66/maven-web-app-project-kk-funda.git'
  }
  stage ('maven build')
  {
   sh  "${mavenHome}/bin/mvn clean package"
  }
   stage ('sonar')
  {
	sh "${mavenHome}/bin/mvn sonar:sonar"
  }
    stage ('nexus report')
  {
    sh "${mavenhome}/bin/mvn clean deploy"
  }

}
