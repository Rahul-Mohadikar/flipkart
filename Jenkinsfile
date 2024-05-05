pipeline{
	agent any 
	parameter{
		choice( name: 'ENV', choices['QA','UAT'], Description: 'pick any environment')}
	trigger {
		pollSCM('* * * * *')
		}
	stages{
		stage('checkout'){
			steps{
				checkout SCM}}
		stage('build'){
			steps{
			sh 'home/rahul/devops/apache-maven-3.9.6'
			echo "bulid has successfully done"}}
		stage('deployment'){
			steps{
			script{
				if ( env.ENV == 'QA'){
				sh 'cp target/flipkart.war home/rahul/devops/apache-tomcat-9.0.88/webapps'
				echo "deployment has been succesfully done!"}
				else ( env.ENV == 'UAT'){
				sh 'cp target/flipkart.war home/rahul/devops/apache-tomcat-9.0.88/webapps'
				else "deployment has been successfully done!"}
				echo "deployment failed"}}}
}}
