node ('new')
{
   stage('Continuous Download ')
  {
    git 'https://github.com/sivatejakavitapu/maven.git'
  }

   stage('Continuous Build ')
  {
   sh 'mvn package'
  }

   stage('Continuous Deploy ')
  {
   deploy adapters: [tomcat9(credentialsId: '95eab3a0-0d96-4a28-a6e2-ee5259f4f079', path: '', url: 'http://172.31.3.160:8080')], contextPath: 'QADeploy', onFailure: false, war: '**/*.war'
  }

   stage('Continuous Testing ')
  {
   git 'https://github.com/sivatejakavitapu/FunctionalTesting.git'
  sh 'java -jar /home/ubuntu/remote/workspace/Scriptedpipeline/testing.jar'
  }

  stage('Continuous Delivery')

  {
   deploy adapters: [tomcat9(credentialsId: '95eab3a0-0d96-4a28-a6e2-ee5259f4f079', path: '', url: 'http://172.31.14.153:8080')], contextPath: 'Proddeploy', onFailure: false, war: '**/*.war'
  }


}
