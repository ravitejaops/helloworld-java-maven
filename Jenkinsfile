node('agent1_linux ') {

  stage ('Checkout'){
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ravitejaops/helloworld-java-maven.git']]])
    }
  stage ('Build') {
    withMaven  {
    sh 'mvn -B -DskipTests clean package'
    }
  }
}
