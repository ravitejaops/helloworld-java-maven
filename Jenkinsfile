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
                   -Dsonar.login=ce0b3326ec9b422e353b9a9e5aee71e41f5c1c50
                   -Dsonar.projectVersion=1.0.0
                   -Dsonar.sources=com.scmgalaxy.mavensample:my-maven/src/main
                   -Dsonar.sourceEncoding=UTF-8
                   -Dsonar.language=java
                   -Dsonar.java.binaries=com.scmgalaxy.mavensample:my-maven/target/classes
                   -Dsonar.tests=com.scmgalaxy.mavensample:my-maven/src/test
                   -Dsonar.junit.reportsPath=com.scmgalaxy.mavensample:my-maven/target/surefire-reports
                   -Dsonar.surefire.reportsPath=com.scmgalaxy.mavensample:my-maven/target/surefire-reports
                   -Dsonar.jacoco.reportPath=com.scmgalaxy.mavensample:my-maven/target/jacoco-it.exec
                   -Dsonar.binaries=com.scmgalaxy.mavensample:my-maven/target/classes
                   -Dsonar.java.coveragePlugin=jacoco
                   -Dsonar.verbose=true'
                }
        }
}
