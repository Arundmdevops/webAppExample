pipeline {
	agent any
		stages {
			stage("git") {
				steps{
					git 'https://github.com/Arundmdevops/webAppExample.git'
				}
			}
			stage("maven build") {
				steps{
					sh "mvn clean install"
                                }
                        }
			stage("deploy on tomcat") {
				steps{
					sshagent(['deploy_user']) {
					sh "scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.231.137.105:/opt/apache-tomcat-10.1.7/webapps"
				  }
			}
		}
	}
}
