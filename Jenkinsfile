node {
    stage('test') {

    echo "Hello"

    }
    
    stage('checkout') {
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ravitejaops/helloworld-java-maven.git']]])
    }
}
