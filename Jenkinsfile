def listBranches() {
    def gitURL = "git@github.com:vshelikhov/jenkins-tests.git"
    def command = "git ls-remote -h $gitURL"

    def proc = command.execute()
    proc.waitFor()

//     if ( proc.exitValue() != 0 ) {
//         println "Error, ${proc.err.text}"
//         System.exit(-1)
//     }

    def branches = proc.in.text.readLines().collect {
        it.replaceAll(/[a-z0-9]*\trefs\/heads\//, '')
    }

    return branches.tokenize()
}
def gitBranches = listBranches()


properties([
//    buildJobs.setBuildDiscarderProperty(),
//    disableConcurrentBuilds(),
//    gitLabConnection('gitlab'),
//    [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false],
//    [$class: 'JobRestrictionProperty'],
    parameters([
//        buildJobs.createReloadPipelineParameter(),
//         listGitBranches(
//             branchFilter: 'origin.*/(.*)',
//             defaultValue: 'default',
//             name: 'nameOfVariable',
//             type: 'BRANCH',
//             remoteURL: env.GIT_URL,
//             credentialsId: GIT_SSH
//         ),
        choice(
            name: 'ACTION',
            choices: gitBranches,
            description: 'Create or destroy existing cluster'
        ),
        choice(
            name: 'COLOR',
            choices: [ "rainbow" ],
            description: 'Cluster color'
        ),
        string(
            defaultValue: '3',
            description: 'Number of master nodes',
            name: 'NEWS1_MASTER_NODES_COUNT'
        ),
        string(
            defaultValue: '3',
            description: 'Number of data nodes',
            name: 'NEWS1_DATA_NODES_COUNT'
        ),
        string(
            defaultValue: '3',
            description: 'Number of master nodes',
            name: 'NEWS15_MASTER_NODES_COUNT'
        ),
        string(
            defaultValue: '6',
            description: 'Number of data nodes',
            name: 'NEWS15_DATA_NODES_COUNT'
        ),
        string(
            defaultValue: 'master',
            description: 'Config repo branch to build from',
            name: 'SOURCE_BRANCH', trim: true
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