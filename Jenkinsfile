node 
{
  def mavenhome=tool name: "maven3.9.9"
  stage ('git checkout')
  { 
    git branch: 'devoplment', credentialsId: 'b9f7ff0f-a9b5-4401-b83d-b5ba2e01514e', url: 'https://github.com/vickyjay66/maven-web-app-project-kk-funda.git'
  }
  stage ('maven build')
  {
   sh  "${mavenhome}/bin/mvn clean package"
  }
   stage ('sonar')
  {
	sh "${mavenhome}/bin/mvn sonar:sonar"
  }
    stage ('nexus report')
  {
    sh "${mavenhome}/bin/mvn clean deploy"
  }
   stage ("tomcat deploying") {
        echo "Deploying WAR file using curl..."

        sh """
            curl -u inam:inam66 \
            --upload-file /var/lib/jenkins/workspace/aws-devops-pipeline/target/maven-web-application.war \
            "http://13.127.196.51:8080/manager/text/deploy?path=/maven-web-application&update=true"
        """
    }


}    
   


  
