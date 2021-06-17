node('master') 
{
    stage('ContinuousDownload') 
    {
       git 'https://github.com/intelliqittrainings/mavennew.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.30.223:/var/lib/tomcat9/webapps/testapp.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
        input 'Waiting for Approval from the DM!'
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.31.112:/var/lib/tomcat9/webapps/prodapp.war'
    }
    
    
    
    
}
