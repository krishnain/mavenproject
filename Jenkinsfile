node('built-in') 
{
    stage('ContinuousDownload')
    {
         git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild')
    {
         sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
         deploy adapters: [tomcat9(credentialsId: 'e8e52507-699e-485c-aa33-b8d5819e0d0e', path: '', url: 'http://172.31.0.42:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
         git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
         sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
         
    }
    stage('ContinuousDelivery')
    {
         deploy adapters: [tomcat9(credentialsId: 'e8e52507-699e-485c-aa33-b8d5819e0d0e', path: '', url: 'http://172.31.8.81:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
    
    
    
    
    
}
