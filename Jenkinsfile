pipeline {
	 agent any

	 stages {
	 stage ('Checkout') {
		steps {
	 git branch:'master', url: 'https://github.com/heyaaronhere/Vulnerable-Web-Application.git'
	 }
 }

 stage('Code Quality Check via SonarQube') {
 steps {
 script {
 def scannerHome = tool 'SonarQube';
 withSonarQubeEnv('SonarQube') {
 sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=OWASP -Dsonar.sources=. -Dsonar.host.url=http://192.168.150.129:9000/"
 }
 }
 }
 }
 }
 post {
 always {
 recordIssues enabledForFailure: true, tool: sonarQube()
 }
 }
}