pipeline {
	agent {
		label 'host'
	}
	stages {
		stage('BUILDandPUBLISH') {
			steps {
				rtMavenResolver (
				    id: 'resolver-id',
				    serverId: 'jfrogserver',
				    releaseRepo: 'libs-release-local',
				    snapshotRepo: 'libs-snapshot-local'
				)
				rtMavenDeployer (
				    id: 'deployer-id',
				    serverId: 'jfrogserver',
				    releaseRepo: 'libs-release-local',
				    snapshotRepo: 'libs-snapshot-local',
				    // By default, 3 threads are used to upload the artifacts to Artifactory. You can override this default by setting:
				    //threads: 6,
				    // Attach custom properties to the published artifacts:
				    //properties: ['key1=value1', 'key2=value2']
				)
				rtMavenRun (
				    // Tool name from Jenkins configuration.
				    tool: 'maven',
				    pom: './pom.xml',
				    goals: 'clean package',
				    // Maven options.
				    //opts: '-Xms1024m -Xmx4096m',
				    resolverId: 'resolver-id',
				    deployerId: 'deployer-id',
				    // If the build name and build number are not set here, the current job name and number will be used:
				    //buildName: 'simplewebapp',
				    //buildNumber: '1'
				)   
			}
		}
	}
}