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
                sh 'mvn package'
            }
        }
        stage(" Deploy on Test") {
            input{
		message "should we continue"
	        ok "yes we should"
	      } 
	   steps {
	    deploy adapters: [tomcat9(credentialsId: 'tomcatserver1', path: '', url: 'http://13.126.181.165:8080')], contextPath: '/app', war: '**/*.war'            }
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

