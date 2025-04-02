pipeline{
	agent any 
	tools
	{
	  maven "maven3.9.9"
	}
	stages{
	stage('gitcheckout'){
	steps{
	   git branch: 'devoplment', credentialsId: '5ddf6198-177c-4cda-97b9-9ba7e0aac8e2', url: 'https://github.com/vickyjay66/maven-web-app-project-kk-funda.git'
	}
	}
	stage('maven compile'){
	steps{
	sh "mvn compile"
	}
	}
	stage('mvnbuild'){
	steps{
	sh "mvn clean package"
	}
	}
	stage('soanarqube'){
	steps{
	sh "mvn sonar:sonar"
	}
	}
	stage('nexus'){
	steps{
	sh "mvn clean deploy"
	}
	}
	stage('tomcat'){
	steps{
	 echo "Deploying WAR file using curl..."
	 sh """
	       curl -u inam:inam66\
	       --upload-file /var/lib/jenkins/workspace/sai-devops/target/maven-web-application.war\
	       "http://13.201.137.182:8080/manager/text/deploy?path=maven-web-application&update=true"
	    """
	}
	}
	}
}
