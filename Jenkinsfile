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
        steps {
		script {
			echo 'Using remote command over ssh'
			sh 'echo "Today is:" date'
			echo '*** Executing remote commands ***'
	 		sh '''#!/bin/bash
				date
				ssh ssh ec2-user@13.233.184.92 << ENDSSH
				java -version
                hostname -i
			    	date
			    	pwd
ENDSSH
'''
                }
            }
        }
    }
