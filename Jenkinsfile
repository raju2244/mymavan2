node('built-in') 
{
stage('continusDownload')
{
    git 'https://github.com/intelliqittrainings/maven.git'
}
stage('continusBuild')
{
    sh 'mvn package'
}
stage('continusDeployment')
{
    deploy adapters: [tomcat9(credentialsId: '19a4d8a1-7605-4310-87f1-8e52b255e46d', path: '', url: 'http://172.31.4.106:8080')], contextPath: 'testapp', war: '**/*.war'
}
stage('continusTesting')
{
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'

    sh 'java -jar /home/ubuntu/.jenkins/workspace/mrk/testing.jar'
}
stage('continusDelivery')
{
  input message: 'need approl from dm', submitter: 'soney'  
    deploy adapters: [tomcat9(credentialsId: 'fb6997e4-2771-496b-9988-0ce46f04e302', path: '', url: 'http://172.31.3.158:8080')], contextPath: 'proadapp', war: '**/*.war'
}

}
