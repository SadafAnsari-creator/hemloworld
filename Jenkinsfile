pipeline {
    agent any
    tools {
        maven 'maven' 
    }
    stages {
        stage("Test") {
            steps {
		sh 'mvn test'
		sh 'mvn --version'
            }
        }
        stage("Build") {
            steps {
                sh 'mvn package'
            }
        }
        stage(" Deploy on Test") {
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

