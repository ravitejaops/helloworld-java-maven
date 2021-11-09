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
                   -Dsonar.login=ce0b3326ec9b422e353b9a9e5aee71e41f5c1c50 \
                   -Dsonar.projectVersion=1.0.0 \
                   -Dsonar.sources=src/main \
                   -Dsonar.sourceEncoding=UTF-8 \
                   -Dsonar.language=java \
                   -Dsonar.java.binaries=target/classes \
                   -Dsonar.tests=src/test \
                   -Dsonar.junit.reportsPath=target/surefire-reports \
                   -Dsonar.surefire.reportsPath=target/surefire-reports \
                   -Dsonar.jacoco.reportPath=target/jacoco.exec \
                   -Dsonar.binaries=**/target/classes \
                   -Dsonar.java.coveragePlugin=jacoco \
                   -Dsonar.verbose=true'
                }
        }
}
