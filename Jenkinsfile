pipeline {
  agent any
   stages{
     stage("Checkout"){
             steps{
                   checkout scm 
                   }
       }
      stage("Build"){
                steps{
                     sh '/home/vboxuser/Documents/DevopsTools/apache-maven-3.9.6/bin/mvn install'
                      }   
                     }
       stage("Deployment"){

                steps{

                    sh 'cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps'
  
                      }
                           }
        }
}
