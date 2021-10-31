node {
  stage ('Build') {
    git url: 'https://github.com/ravitejaops/helloworld-java-maven'
    withMaven  {
    sh 'mvn -B -DskipTests clean package'
    }
  }
}
