//
// properties([
//     parameters([
//         listGitBranches(
//             name: 'FROM_BRANCH',
//             description: 'some shit',
//             remoteURL: env.GIT_URL, //'git@github.com:vshelikhov/jenkins-tests.git',
//             credentialsId: 'GITHUB_SSH'
//         )
//     ])
// ])
//
//

pipeline {
    agent {
        label '!windows'
    }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('Build') {
            steps {
                sh 'printenv'
            }
        }
    }
}