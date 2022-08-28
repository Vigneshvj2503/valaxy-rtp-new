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
        stage('execute') {
		steps {
		script {
			echo 'Using remote command over ssh'
			sh 'echo "Today is:" date'
			echo '*** Executing remote commands ***'
	 		sh '''#!/bin/bash
				date
				ssh ec2-user@13.233.184.92 << ENDSSH
				hostname -i
				java -version
			    	date
			    	cd /tmp
			    	pwd
ENDSSH
'''

			sh '''
				date
				ssh ec2-user@13.233.184.92 << ENDSSH
				hostname -i
				javac -version
				date
				cd /tmp
				pwd
ENDSSH
'''
                }
            }
        }
    }
}
