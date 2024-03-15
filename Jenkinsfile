pipeline {
	agent any
	
	parameters {
		choice(name: 'ENVIRONMENT', choices: ['QA','UAT'], description: 'Pick Environment value')
	}
	stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh '/home/dhairya/devops/apache-maven-3.9.6-bin/apache-maven-3.9.6/bin/mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			script {
			 if ( env.ENVIRONMENT == 'QA' ){
        	sh 'cp target/CICD.war /home/dhairya/devops/apache-tomcat-8.5.99/webapps'
        	echo "deployment has been done on QA!"
			 }
			elif ( env.ENVIRONMENT == 'UAT' ){
    		sh 'cp target/CICD.war /home/dhairya/devops/apache-tomcat-8.5.99/webapps'
    		echo "deployment has been done on UAT!"
			}
			echo "deployment has been done!"
			fi
			
			}}}	
}}
