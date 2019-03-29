node('master') 
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/MuraliKarre/maven.git'
    }
    
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    
    stage('ContinuousDeployment')
    {
        sh 'scp /var/lib/jenkins/workspace/demo/webapp/target/webapp.war ubuntu@13.233.93.49:/opt/tomcat/webapps/qaenv.war'
    }
    
    stage('ContinuousTesting')
    {
    
        git 'https://github.com/MuraliKarre/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/demo/testing.jar'
    }
        stage('ContinuousDelivery')
    {
        input message: 'Waiting for Delivery', submitter: 'admin'
        sh 'scp /var/lib/jenkins/workspace/demo/webapp/target/webapp.war ubuntu@13.233.93.49:/opt/tomcat/webapps/prodenv.war'
    }
    

    
    
    
    
   
}
