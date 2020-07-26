pipeline {
    agent any
    tools {
        maven 'maven_3.6.3' 
    }
    stages 
    {
        stage('build') {
            
            	steps{
            			bat 'mvn -f ProducerService/pom.xml -DskipTests=true package'
            		}
            }
            
         stage('deploy')
         {
         		steps{
         				withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'PCF_LOGIN',
						usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) 
						{

							bat 'cf login -a https://api.run.pivotal.io -u gomathyuc29@gmail.com -p Abhi29@lash'
							bat 'cf target -s ascend-test-space'
							bat 'cf push -f ProducerService/manifest.yml'
 						}
         
         			}
         	
         }
     }
}