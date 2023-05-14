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
          script {
            sh 'mvn package'
            echo "building the app"  
            withCredentials([usernamePassword(credentialsId: '1dad4981-b3c5-45f8-a121-e0481ec0c5c0', passwordVariable: 'PASS', usernameVariable: 'USER')])
                sh 'docker build -t java-maven-app:2.0 .' 
                sh 'echo $PASS | docker login -u $USER --password-stdin'
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
