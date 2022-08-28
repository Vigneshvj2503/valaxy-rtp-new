pipeline {
    agent {
       node {
         label "slave"
      }
    }
    stages {
        stage('Build') {
            steps {
                echo '<--------------- Building --------------->'
                sh 'printenv'
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo '<------------- Build completed --------------->'
            }
        }
		stage ('Deploy') {
			steps{
				//sshagent(credentials : ['deployment']) {
				sshPublisher(publishers: [sshPublisherDesc(configName: 'deploymentserver', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'nohup java -jar demo-workshop-2.0.1.jar &', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/home/ec2-user/application', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
				//}
			}
		}
    }
}
