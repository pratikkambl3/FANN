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
                  sh 'if ( env.ENV == "DEV" ){
                   echo "Deployed to DEV"'                   
 cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps'}'
                 sh 'else ( env.ENV == "QA" ) {
                   echo "Deployed to QA"'
                    cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps'
            }
                   sh 'else ( env.ENV == "UAT" ) {
                   echo "Deployed to UAT"'
                   cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps'
                          }             
  }
                   }
                           }
        }
}
