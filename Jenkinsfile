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
				sshagent(credentials : ['deployment']) {
				sh 'scp /home/ec2-user/.m2/repository/com/stalin/demo-workshop/2.0.1/demo-workshop-2.0.1.jar ec2-user@13.233.184.92:/home/ec2-user/application/'
				sh 'ssh -o StrictHostKeyChecking=no ec2-user@13.233.184.92 nohup java -jar demo-workshop-2.0.1.jar &'
				}
			}
		}
    }
}
