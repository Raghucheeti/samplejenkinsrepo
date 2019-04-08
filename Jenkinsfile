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
    stage('email'){
        timeout(time: 30, unit: 'MINUTES') {
        input message: 'Do you want to Deploy?', ok: 'Deploy'
        sh "mutt -s 'The job is completed' deepaklama0815@gmail.com"
     }
    }
    // stage('backup JAR file'){
    //     withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-test-key', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
    //     sh "aws s3 cp target/my-app-1-RELEASE.jar s3://test-only-123/"
    //     }
    // } this is just a comment
    //stage('deployment'){
        //sshagent(['demo-ssh-key']) {
        //sh "scp -o StrictHostKeyChecking=no target/my-app-1-RELEASE.jar deployuser@54.196.23.241:/home/deployuser/"
      // }
//}
    }

