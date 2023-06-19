pipeline{
    agent any
    tools {
      maven 'maven'
    }
    stages{
        stage("BUILD"){
            steps{
                sh'mvn --version'
                echo "========executing A========"
            }
           
        }
        stage("TESt"){
            steps{
                echo "========executing A========"
            }
           
        }
    
        stage("PRODUCTION"){
            steps{
                echo "========executing A========"
            }
           
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
