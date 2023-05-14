def gv
pipeline {
  
     agent any 
     parameters { 
        choice(name: 'VERSION', choices: ['1.3', '2.1'], description: 'choose from the choices')
        booleanParam(name: 'executeTest', defaultValue: true, description: 'this is the defaul value')
   
     }
   
     stages {
       stage("init") {
         steps {
           script {
             gv = load "script.groovy"
           }
         
         }
       
      
       }
      stage("build") {
        input {
        message "Select the env you want to deply on"
         ok "Doneo"
          parameters { 
        choice(name: 'env', choices: ['test', 'prod'], description: 'choose from the choices')
   
     }
        
        }
        
        steps {
          echo "building the app"  
        
        }
           
     }
    
      stage("test") {
        steps {
         echo "testing the app"  
         when {
             expression {
             params.executetest
                  
           }
                
         }
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
