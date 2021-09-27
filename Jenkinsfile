properties([
    buildJobs.setBuildDiscarderProperty(),
    disableConcurrentBuilds(),
    gitLabConnection('gitlab'),
    [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false],
    [$class: 'JobRestrictionProperty'],
    parameters([
        buildJobs.createReloadPipelineParameter(),
        choice(
            name: 'REGION',
            choices: availableRegions,
            description: 'Region'
        ),
        listGitBranches(
            branchFilter: 'origin.*/(.*)',
            defaultValue: 'default',
            name: 'nameOfVariable',
            type: 'BRANCH',
            remoteURL: GIT_URL,
            credentialsId: GIT_CREDS_ID
        ),
        choice(
            name: 'ACTION',
            choices: ['apply','destroy'],
            description: 'Create or destroy existing cluster'
        ),
        choice(
            name: 'COLOR',
            choices: [ "rainbow" ],
            description: 'Cluster color'
        ),

        choice(
            name: 'NEWS1_MASTER_INSTANCE_TYPE',
            choices: ec2InstanceConfig.instanceTypesMaster,
            description: 'News1 MASTER EC2 instance type'
        ),
        choice(
            name: 'NEWS1_DATA_INSTANCE_TYPE',
            choices: ec2InstanceConfig.instanceTypesData,
            description: 'News1 DATA EC2 instance type'
        ),
        choice(
            name: 'NEWS15_MASTER_INSTANCE_TYPE',
            choices: ec2InstanceConfig.instanceTypesMaster,
            description: 'News15 MASTER EC2 instance type'
        ),
        choice(
            name: 'NEWS15_DATA_INSTANCE_TYPE',
            choices: ec2InstanceConfig.instanceTypesData,
            description: 'News15 DATA EC2 instance type'
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

