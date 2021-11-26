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
               withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'sonarqubeid') {
                sh 'mvn clean org.jacoco:jacoco-maven-plugin:0.7.4.201502262128:prepare-agent install sonar:sonar \
                   -Dsonar.projectKey=com.scmgalaxy.mavensample:my-maven \
                   -Dsonar.host.url=http://18.133.170.11:9000/sonar \
                   -Dsonar.login=5419221bfccb23b9825ed2bf304d20025cb8e6a9 \
                   -Dsonar.projectVersion=1.0.0 \
                   -Dsonar.sources=src/main/java/ \
                   -Dsonar.sourceEncoding=UTF-8 \
                   -Dsonar.language=java \
                   -Dsonar.java.binaries=target/classes/ \
                   -Dsonar.tests=src/test \
                   -Dsonar.junit.reportPaths=target/surefire-reports/ \
                   -Dsonar.surefire.reportPaths=target/surefire-reports/ \
                   -Dsonar.jacoco.reportPaths=target/jacoco.exec \
                   -Dsonar.verbose=true'
                }
        }
}
