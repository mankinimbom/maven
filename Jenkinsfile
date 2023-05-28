node('built-in') 
{
    stage('ContinuuousDownload') 
    {
       git 'https://github.com/mankinimbom/maven.git'
    }
    stage('ContinuuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://4.227.254.138:8080')], contextPath: 'paradigm', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
          git 'https://github.com/mankinimbom/testingproject.git'
          sh 'java -jar /var/lib/jenkins/workspace/tests/testing.jar'
    }
    stage('ContinuousDelivery')
    {
            deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://4.227.254.138:8080')], contextPath: 'paradigm', war: '**/*.war'
    }
    stage('ContinuousMonitor')
    {
        
    }}
