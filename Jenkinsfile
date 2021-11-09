node() {

  stage ('Checkout'){
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ravitejaops/helloworld-java-maven.git']]])
    }
  /*stage ('Build') {
    withMaven  {
    sh 'mvn -B -DskipTests clean package'
    }
  }*/
  
  stage ('Scan and Build Jar File') {
               withSonarQubeEnv(installationName: 'sonarqubeJenkins', credentialsId: 'sonarJenkins') {
                sh 'mvn clean package sonar:sonar \
                   -Dsonar.projectKey=com.scmgalaxy.mavensample:my-maven \
                   -Dsonar.host.url=http://35.179.15.141:9090/sonar \
                   -Dsonar.login=ce0b3326ec9b422e353b9a9e5aee71e41f5c1c50'
                }
        }
}
