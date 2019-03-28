node('maven'){
    def mvnHome = tool name: 'maven360', type: 'maven'
    stage('checkout1'){
    git credentialsId: 'githubaccount', url: 'https://github.com/deepaklama0815/samplejenkinsrepo.git'
    }
    stage('test'){
        sh "${mvnHome}/bin/mvn clean test surefire-report:report-only"
        junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
        archiveArtifacts allowEmptyArchive: true, artifacts: 'target/surefire-reports/*'
        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site/', reportFiles: 'surefire-report.html', reportName: 'HTMLReport', reportTitles: ''])
    }
    stage('package'){
        sh "${mvnHome}/bin/mvn clean package -Dskiptest"
    }
}
