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
      stage('SonarQube analysis') {
		steps{			
			def scannerHome = tool name: 'Sonar-4', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
			echo "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=Jurisprudencia_ORCTXT -Dsonar.sources=. -Dsonar.login=69d977f11910740d9ca95b75cede210db01489c9"
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
