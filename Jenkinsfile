node('ec2linux') {

  stage ('Checkout'){
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ravitejaops/helloworld-java-maven.git']]])
    }
  /*stage ('Build') {
    withMaven  {
    sh 'mvn -B -DskipTests clean package'
    }
  }*/
  
  stage ('Scan and Build Jar File') {
            steps {
               withSonarQubeEnv(installationName: 'sonarqubeJenkins', credentialsId: 'sonarJenkins') {
                sh 'mvn clean package sonar:sonar'
                }
            }
        }
}
