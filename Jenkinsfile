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
def notifyBuild(String buildStatus = 'STARTED') {
    buildStatus = buildStatus ?: 'SUCCESS'

    def colorName = 'RED'
    def colorCode = '#FF0000'
    def subject = "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
    def summary = "${subject} (${env.BUILD_URL})"

    if (buildStatus == 'STARTED') {
        colorName = 'YELLOW'
        colorCode = '#FFFF00'
    } else if (buildStatus == 'SUCCESS') {
        colorName = 'GREEN'
        colorCode = '#00FF00'
    }

    slackSend (color: colorCode, message: summary)
}
