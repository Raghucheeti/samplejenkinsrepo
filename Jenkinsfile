node('maven'){
    def mvnhome = tool name: 'maven360', type: 'maven'
echo "downloading the source code"
stage('checkout'){
git credentialsId: 'githubaccount', url: 'https://github.com/deepaklama0815/samplejenkinsrepo.git'
}
stage('test'){
    echo "executing test cases"
    sh "$mvmhome/bin/mvn clean test"

}
}
