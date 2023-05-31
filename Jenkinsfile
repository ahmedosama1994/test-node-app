@Library('jenkins--shared-library')

def gv
pipeline {
  
     agent any 
    tools {
    maven 'MVN'
  }
     parameters { 
        choice(name: 'VERSION', choices: ['1.3', '2.1'], description: 'choose from the choices')
        booleanParam(name: 'executeTest', defaultValue: true, description: 'this is the defaul value')

   
     }
   
     stages {
       stage("init") {
         steps {
           script {
            build-jar() 
             
           }
         
         }
       
      
       }
      stage("building the docker image") {
      
      when {
      expression {
      
      BRANCH_NAME == 'master'
      
      }
      
      
      }
       
        steps {
          
          
            echo "building the app"  
            
        }
           
     }
    
      stage("test") {
        steps {
         echo "testing the app"  
         
       }
            
     }
      
     stage("deploy") {
       steps {
         echo "deploying the app"  
         echo "deploying version ${params.VERSION}"
        
       }     
     }            
  }  
}
