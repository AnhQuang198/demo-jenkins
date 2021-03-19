node {
    def mvnHome = tool 'maven-3.6.2'
    try {
        switch (env.BRANCH_NAME) {
            case 'develop':
                stage('clone') {
                    git 'https://github.com/AnhQuang198/demo-jenkins.git'
                    mvnHome = tool 'maven-3.6.2'
                }
                stage('build-dev') {
                    sh "'${mvnHome}/bin/mvn' clean install"
                }
                stage('log') {
                    echo 'build end in develop branch!'
                }
                break
            case 'master':
                stage('build') {
                    echo 'build in branch master'
                }
                break
        }
    } catch (e) {
        currentBuild.result = "FAILED"
        throw e
    }
}