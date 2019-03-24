node('maven'){
    def mvnHome = tool name: 'maven360', type: 'maven'
    stage('checkout'){
    git credentialsId: 'githubaccount', url: 'https://github.com/deepaklama0815/samplejenkinsrepo.git'
    }
    stage('test'){
        sh "${mvnHome}/bin/mvn clean test"
        junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
        archiveArtifacts allowEmptyArchive: true, artifacts: 'target/surefire-reports/*'
    }
    stage('package'){
        sh "${mvnHome}/bin/mvn clean package -Dskiptest"
    }
}
