pipeline {
  agent any
   parameters {
  choice choices: ['DEV', 'QA', 'UAT'], name: 'ENV'
       }
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
                Script {
                   if ( env.ENV == "DEV" ){
                   sh 'echo "Deployed to DEV"'                   
 sh 'cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps'}
                   else ( env.ENV == "QA" ) {
                   sh 'echo "Deployed to QA"'
                   sh 'cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps'
            }
                   else ( env.ENV == "UAT" ) {
                   sh 'echo "Deployed to UAT"'
                   sh 'cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps'
                          }             
  }
                   }
                           }
        }
}
