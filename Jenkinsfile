node('maven'){
    def mvnHome = tool name: 'maven360', type: 'maven'
    echo "downloading scmm"
    stage('checkout'){
    git credentialsId: 'githubaccount', url: 'https://github.com/deepaklama0815/samplejenkinsrepo.git'
    }
    stage('test'){
        sh "mvnHome/bin/mvn clean test"
    }
}


