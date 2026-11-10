pipeline {
	agent any
	environment {
	PATH="/opt/maven/bin:$PATH"
	}
	
	stages {
	   stage('build') {
		steps {
                  echo '...build started.....'
		  sh 'mvn clean package -Dmaven.test.skip=true'
                  echo '...build completed...'
		}	
	   }
           stage('test') {
                steps {
                  echo '...test started.....'
                  sh 'maven-surefire-report:report'
                  echo '...test completed...'
                }	
           }
           stage('SonarQube-Analsys') {
		environment {
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
