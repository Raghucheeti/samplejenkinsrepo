node('maven'){
    def mvnHome = tool name: 'maven360', type: 'maven'
    stage('checkout'){
    git credentialsId: 'githubaccount', url: 'https://github.com/deepaklama0815/samplejenkinsrepo.git'
    }
    stage('build'){
        sh "mvnHome/bin/mvn clean test"
    }
    stage('package'){
        sh "mvnhome/bin/mvn clean package"
    }
}
