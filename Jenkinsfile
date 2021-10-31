node {
  stage ('Build') {
    //git url: 'https://github.com/ravitejaops/helloworld-java-maven'
    //withMaven {
    //  sh "mvn clean verify"
    //} // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
    withMaven  {
    //sh 'mvn -B -DskipTests clean package'
    sh "mvn clean verify"
    }
  }
}
