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
 sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=OWSAP -Dsonar.sources=. -Dsonar.host.url=http://192.168.150.129:9000 -Dsonar.login=b35789c1a58afce555f1050479a86e343899684f"
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