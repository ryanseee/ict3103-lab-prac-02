pipeline {
	agent any
	tools {
		nodejs "node"
		jdk "openjdk-11"
		maven "Maven 3.6.3"
	}
	stages {
		stage('Code Quality Check via SonarQube') {
			script {
				def scannerHome = tool 'SonarQube'
				withSonarQubeEnv() {
					sh "${tool("SonarQube")}/bin/sonar-scanner \
					-Dsonar.projectKey=ict3103-labPrac-02 \
					-Dsonar.sources=. \
					-Dsonar.host.url=http://47.254.255.197:9000 \
					-Dsonar.login=0f8c6f7195a6cfcdef84dba521c51885e54cd221"
				}
		}
	}
	post {
		always {
			recordIssues enabledForFailure: true, tool: sonarQube()
		}
	}
}