pipeline{
    agent any
    tools{
     maven 'maven'
    }
    stages{
      stage(test){
          steps{
              sh 'mvn test' 
          }
       }
      stage(build){
          steps{
              sh 'mvn package'
          }
       }
      stage(deploy){
          steps{
              deploy adapters: [tomcat9(path: '', url: 'http://43.205.239.19:8080')], contextPath: '/app', war: '**/*.war'
          }
       }
      post { 
        always { 
            echo 'I will always say Hello again!'
        }
         failure { 
            echo 'I will always when fail!'
        }
         success { 
            echo 'I will always when sucess!'
        }
      } 
    }
  }
