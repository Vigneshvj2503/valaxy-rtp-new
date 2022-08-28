def version   = '1.0.3'
def app
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
        /**stage(" Deploy ") {
          steps {
            script {
               echo '<--------------- Deploy Started --------------->'
               sh './deploy.sh'
               echo '<--------------- Deploy Ends --------------->'
            }
          }
        }**/

    }
 }
