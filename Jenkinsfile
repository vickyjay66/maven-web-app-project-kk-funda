node 
{
  def mavenhome=tool name:"maven3.9.9"

  stage ('git checkot')
  {

   git branch: 'devoplment', credentialsId: '5ddf6198-177c-4cda-97b9-9ba7e0aac8e2', url: 'https://github.com/vickyjay66/maven-web-app-project-kk-funda.git'
  }

  stage ('maven build')
  {
    sh "${mavenhome}/bin/mvn clean package"

  }

  stage('sonar qube')
  {

  sh "${mavenhome}/bin/mvn sonar:sonar"
  
  }

  stage('nexus')
  {

  sh "${mavenhome}/bin/mvn clean deploy"
  }
  
  stage('tomcat'){
   echo "Deploying WAR file using curl..."

    sh """ 
          curl -u inam:inam66 \
          --upload-file /var/lib/jenkins/workspace/sai.devops/target/maven-web-application.war \
          "http://13.201.137.182:8080/manager/text/deploy?path=maven-web-application&update=true"
      """
  }


}
