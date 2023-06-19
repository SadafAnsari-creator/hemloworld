pipeline{
    agent any
    tools {
     maven 'maven'
    }
    stages{
        stage("BUILD"){
            steps{
                sh 'mvn package'
            }
           
        }
        stage("TESt"){
            steps{
                sh 'mvn test'
            }
           
        }
    
        stage("PRODUCTION"){
            steps{
                 deploy adapters: [tomcat9(credentialsId: 'tomcatserver', path: '', url: 'http://43.204.228.27:8080')], contextPath: '/app', war: '**/*.war'            }
           
        } 
    
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
