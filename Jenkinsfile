pipeline {
    agent any
    tools {
        maven 'maven3'        
    }
    stages {
      stage('SCM Chekout'){
          steps {
             echo 'Code checkout from GIT'
             git credentialsId: 'GitSSHKey', url: 'https://github.com/SatishDevops01/SonarRepo', branch: 'master'
          }
      }
      stage('Code Analysis'){
         steps {
              echo 'Static code analysis using SonarQube'
              withSonarQubeEnv('Sonar-4') {
			  echo 'mvn sonar:sonar'
	      }
         }     
      } 
      stage('Build Packages'){
          steps {
              echo 'Build the packages using Maven'
              echo "mvn clean package"
          }     
      } 
   
   }
}
