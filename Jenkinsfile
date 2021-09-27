
properties([
    parameters([
        listGitBranches(
            name: 'FROM_BRANCH',
            description: 'some shit'
            remoteURL: env.GIT_URL, //'git@github.com:vshelikhov/jenkins-tests.git',
            credentialsId: 'GITHUB_SSH'
        )
    ])
])



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
//                echo "Database engine is ${DB_ENGINE}"
//                echo "DISABLE_AUTH is ${DISABLE_AUTH}"
                sh 'printenv'
            }
        }
    }
}