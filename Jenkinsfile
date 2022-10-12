pipeline {
    agent any
    tools {
        maven 'maven3' 
	sonar 'Sonar-4'
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
			echo "sonar-scanner -Dsonar.projectKey=maven-basic -Dsonar.sources=src"
			
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
