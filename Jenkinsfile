pipeline {
  agent any
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
                     sh '/home/pratikkambl3/Documents/Devops-Tools/apache-maven-3.9.6/bin/mvn install'

			}   
                     }
       stage("Deployment"){

                steps{
                
                  sh '''if  [  $ENV  =  "QA"  ];then
echo "Deployed to QA"
scp target/FANN.war /home/pratikkambl3/Documents/Devops-Tools/apache-tomcat-9.0.89/webapps

elif  [$ENV = "DEV" ];then
echo "Deployed to DEV"
cp target/FANN.war /home/pratikkambl3/Documents/Devops-Tools/apache-tomcat-9.0.89/webapps

elif [$ENV = "UAT" ];then
echo "Deployed to UAT"
cp target/FANN.war /home/pratikkambl3/Documents/Devops-Tools/apache-tomcat-9.0.89/webapps

fi
'''          
  
                   }
                           }
           stage("Notification"){
                     steps{
                              slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#amazon', color: 'good', message: 'Welcome to jenkins slack notification', teamDomain: 'DEVOPS', tokenCredentialId: '198aa9be-1475-4586-ba77-716050239d16'
                                 }
                          }
        }
}
