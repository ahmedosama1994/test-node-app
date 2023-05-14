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
             gv = load "script.groovy"
           }
         
         }
       
      
       }
      stage("building the docker image") {
       
        steps {
          
            sh 'mvn package'
            echo "building the app"  
            withCredentials([usernamePassword(credentialsId:'dockerhubb', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')])
          {

                sh 'docker build -t java-maven-app:2.0 .' 
                sh 'echo $PASSWORD | docker login -u $USERNAME --password-stdin'
                sh 'docker push java-maven-app:2.0'
          
          }
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
