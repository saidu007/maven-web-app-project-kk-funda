pipeline {
	agent any
tools
{
	maven "maven-3.9.9"
}
	stages {
		stage('checkout stage') {
			steps {
			git credentialsId: '4bd90d5a-91f2-49d9-94d9-c39c90336058', url: 'https://github.com/saidu007/maven-web-app-project-kk-funda.git'
			}
		}
		stage('Build') {
			steps {
		sh "mvn clean package"	
			}
		}
		/*stage('SQ Report') {
			steps {
		sh "mvn sonar:sonar"
			}
		}
		stage('Deploy to Nexus') {
			steps {
		sh "mvn clean deploy"
			}
		}
		stage('Deploy to Tomcat') {
			steps {
		echo "Deploynig WAR file using curl command..."
			sh """
				  curl -u saidulu:!Siddukala2015 \
  --upload-file /var/lib/jenkins/workspace/jio-scripted-way/target/maven-web-application.war \
  "http://52.64.253.191:8080/manager/text/deploy?path=/maven-web-application/&update=true"
"""
}
}*/
		
	} //stages closing		
/*post {
  success {
    notifyBuild(currentBuild.result)
  }
  failure {
notifyBuild(currentBuild.result)
      }
}*/
}//pipeline closing


/*def notifyBuild(String buildStatus = 'STARTED') {
  // build status of null means successful
  buildStatus =  buildStatus ?: 'SUCCESS'

  // Default values
  def colorName = 'RED'
  def colorCode = '#FF0000'
  def subject = "${buildStatus}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'"
  def summary = "${subject} (${env.BUILD_URL})"

  // Override default values based on build status
  if (buildStatus == 'STARTED') {
    color = 'YELLOW'
    colorCode = '#FFFF00'
  } else if (buildStatus == 'SUCCESS') {
    color = 'GREEN'
    colorCode = '#00FF00'
  } else {
    color = 'RED'
    colorCode = '#FF0000'
  }

  // Send notifications
  slackSend (color: colorCode, message: summary, channel: '#airtel-dev')
}*/	
	
