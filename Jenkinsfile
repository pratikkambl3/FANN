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
                
                  sh '''if  [  $ENV  =  "QA"  ];then
echo "Deployed to QA"
cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps
elif  [$ENV = "DEV" ];then
echo "Deployed to DEV"
cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps
elif [$ENV = "UAT" ];then
echo "Deployed to UAT"
cp target/FANN.war /home/vboxuser/Documents/DevopsTools/apache-tomcat-9.0.88/webapps
fi
'''          
  
                   }
                           }
        }
}
