pipeline {
  
     agent any 
     Parameters { 
        choice(name: 'VERSION', choices: ['1.3', '2.1'], description: 'choose from the choices')
        booleanParam(name: 'executeTest', defaultValue: true, description: 'this is the defaul value')
   
     }
   
  
 
  stages {
    
    stage("build") {
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
