pipeline {
    agent any
    tools {
        maven 'maven3' 
        sonar 'sonarqube-8.9.9'
    }
    stages {
      stage('SCM Chekout'){
          steps {
             echo 'Code checkout from GIT SCM'
             git credentialsId: 'GitSSHKey', url: 'https://github.com/SatishDevops01/MavenRepo'
          }
      }
      stage('Build Package'){
          steps {
              echo 'Build the packages using Maven'
              echo "mvn clean install"
          }     
      } 
      stage('SonarQube Analysis'){
         steps {
              echo 'Build the packages using Maven'
              withSonarQubeEnv('sonarqube-8.9.9') {
		  echo 'mvn sonar:sonar'
	      }
         }     
      }    
   }
}
