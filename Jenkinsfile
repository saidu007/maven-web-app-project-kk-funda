node 
{
 echo "git branch name: ${env.JOB_NAME}"
   echo "build number is: ${env.BUILD_NUMBER}"
   echo "node name is: ${env.NODE_NAME}"
   def mavenHome=tool name: "maven-3.9.9"
 try {		
	stage('git checkout')
	{ notifyBuild('STARTED')
		git credentialsId: '4bd90d5a-91f2-49d9-94d9-c39c90336058', url: 'https://github.com/saidu007/maven-web-app-project-kk-funda.git'
	}
	stage('Compile')
	{
	 sh	"${mavenHome}/bin/mvn compile"
	}
	stage('Build')
	{
	 sh	"${mavenHome}/bin/mvn clean package"
	}
	/*stage('SQ Report')
	{
	 sh	"${mavenHome}/bin/mvn sonar:sonar"
	}
	stage('Deploy to Nexus')
	{
	 sh	"${mavenHome}/bin/mvn clean deploy"
	}
	stage('Deploy to tomcat')
	{
	 echo "Deploy WAR file using curl...."
	sh """
  curl -u saidulu:!Siddukala2015 \
  --upload-file /var/lib/jenkins/workspace/jio-scripted-way/target/maven-web-application.war \
  "http://52.64.253.191:8080/manager/text/deploy?path=/maven-web-application/&update=true"
"""
	 
	}*/
  } catch (e) {
       currentBuild.result = "FAILED"
       throw e
   } finally {
       notifyBuild(currentBuild.result)
   }
}

