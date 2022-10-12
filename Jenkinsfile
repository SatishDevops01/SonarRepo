pipeline {
    agent any
	environment {
        scannerHome = tool 'sonar4'
    }
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
      stage('SonarQube analysis') {
		steps{	
			echo 'SonarQube Analysis start'	
			withSonarQubeEnv('sonarqube') {
            		echo "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=maven-basic -Dsonar.sources=src"
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
