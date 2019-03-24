node('maven'){
    def mvnHome = tool name: 'maven360', type: 'maven'
    stage('checkout'){
    git credentialsId: 'githubaccount', url: 'https://github.com/deepaklama0815/samplejenkinsrepo.git'
    }
    stage('test'){
        sh "${mvnHome}/bin/mvn clean test surefire-reports:report-only"
        junit allowEmptyResults: true, testResults: 'target/*.jar'

    }
    stage('package'){
        sh "${mvnHome}/bin/mvn clean package -Dskiptest"
    }
}
