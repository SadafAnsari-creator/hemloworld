pipeline {
    agent any
    tools {
        maven 'maven' 
    }
    stages {
        stage("Test") {
            steps {
		sh 'mvn --version'
		sh 'mvn test'
		
            }
        }
        stage("Build") {
            steps {
                sh 'mvn clean install'
            }
        }
        stage(" Deploy on Test") {
            input{
		message "should we continue"
	        ok "yes we should"
	      } 
	   steps {
	    deploy adapters: [tomcat9(credentialsId: 'tomcatserver', path: '', url: 'http://43.205.239.19:8080')], contextPath: '/app', war: '**/*.war'      
	   }
          }
        }  
	post{
	    always{
		 echo "=========always====="
		} 
            success{
		  echo "=========pipeline executed successfully====="
		}
            failure{
	      echo "=========pipeline execution failed====="
		}		
	
	}
}

