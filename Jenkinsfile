pipeline {
	agent any
	environment {
	PATH="/opt/maven/bin:$PATH"
	}
	
	stages {
	   stage('build') {
		steps {
		  sh 'mvn clean package'
		}	
	   }	
           stage('SonarQube-Analsys') {
		enviroment {
		sonarHome =tool 'saidemy-sonarqube-scanner'
		}
		steps {
		  withSonarQubeEnv('saidemy-sonarqube-server') {
		  sh "${sonarHome}/bin/sonar-scanner"
  		  }	
		}
           }
        }
}   
