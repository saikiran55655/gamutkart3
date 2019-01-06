pipeline {
	agent any

	stages {
	    stage('Checkout') {
	        steps {
				checkout scm			        }
		    }
		stage('Build') {
	        steps {
//				sh '${MAVEN_HOME}/bin/mvn install'
				sh '/home/kiran/distros/apache-maven-3.3.9/bin/mvn install'
	        }
		}
                stage('Deployment') {
                      steps {
                            sh 'sshpass -p "55655" scp target/gamutkart.war kiran@172.17.0.3:/home/kiran/distros/apache-tomcat-8.5.35/webapps'                    }
                 }
         stage('Startup') {
                       steps {
                         sh 'sshpass -p "55655" ssh kiran@172.17.0.3 JAVA_HOME=/home/kiran/distros/jdk1.8.0_191 /home/kiran/distros/apache-tomcat-8.5.35/bin/startup.sh'
                 }

         }
	}
}

