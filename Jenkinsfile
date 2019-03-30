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
    //stage('email'){
    //   sh "mutt -s "The job is completed" deepaklama0815@gmail.com"
    //}
    stage('deployment'){
        sshagent(['demo-ssh-key']) {
        sh "scp -o StrictHostKeyChecking=no target/my-app-1-RELEASE.jar deployuser@52.91.69.147:/home/deployuser/"
      // sh "scp -o StrictHostKeyChecnking=no my-app.jar deployuser@52.91.69.147:~/deployuser/"
       }
    }
}
