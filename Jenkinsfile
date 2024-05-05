pipeline{
	agent any 
	parameters{
		choice( name: 'ENV', choices:['QA','UAT'], description: 'pick any environment')}
	triggers {
		pollSCM('* * * * *')
		}
	stages{
		stage('cleanup workspace'){
			steps{
				cleanWS()
				echo "cleanup workspace for flipkart"
				}}
		stage('checkout'){
			steps{
				checkout scm}}
		stage('build'){
			steps{
				sh '/home/rahul/devops/apache-maven-3.9.6/bin/mvn install'
				echo "bulid has successfully done"}}
		stage('deployment'){
			steps{
				script{
					if ( env.ENV == 'QA' ){
					sh 'cp flipkart.war /home/rahul/devops/apache-tomcat-9.0.88/webapps'
					echo "deployment has been succesfully done!"}
					else ( env.ENV == 'UAT' ){
					sh 'cp flipkart.war /home/rahul/devops/apache-tomcat-9.0.88/webapps'
					echo "deployment has been successfully done!"}
			}}}
}}
