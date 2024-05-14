pipeline {
  agent {
	label 'blue'
	}
   parameters {
  choice choices: ['DEV', 'QA', 'UAT'], name: 'ENV'
       }
    triggers {
  pollSCM '* * * * *'
   }
   stages{
     stage("Checkout"){
             steps{
                   checkout scm 
                   }
       }
      stage("Build"){
                steps{
                     sh '/home/grras/project/apache-maven-3.9.6/bin/mvn install'

			}   
                     }
       stage("Deployment"){

                steps{
                
                  sh '''if  [  $ENV  =  "QA"  ];then
echo "Deployed to QA"
scp target/FANN.war /home/pratikkambl3/Documents/Devops-Tools/apache-tomcat-9.0.89/webapps

elif  [$ENV = "DEV" ];then
echo "Deployed to DEV"
scp target/FANN.war /home/pratikkambl3/Documents/Devops-Tools/apache-tomcat-9.0.89/webapps

elif [$ENV = "UAT" ];then
echo "Deployed to UAT"
scp target/FANN.war /home/pratikkambl3/Documents/Devops-Tools/apache-tomcat-9.0.89/webapps

fi
'''          
  
                   }
                           }
        }
}
