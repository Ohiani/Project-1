pipeline{
    agent any

    stages{

        stage('Checkout SCM') {
            steps{
                git branch: 'main', url: 'https://github.com/Ohiani/Project-1.git'
                   }
            }
        
        stage("Deploy"){
            steps{
                withCredentials([sshUserPrivateKey(credentialsId: 'project14', keyFileVariable: 'SSH_KEY')]) {
                    // SSH connection to the remote server
                    sh '''
                        ssh -i $SSH_KEY ubuntu@13.40.4.139 cd /var/www/html && \
                        git pull origin main && \
                        sudo service apache2 restart'''
                        
                }

            }
          }
  }
}
