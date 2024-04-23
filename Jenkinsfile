pipeline {
    agent any
    stages {
        stage('Pulling Changes') {
            steps {
                script {
                    sshagent(credentials: ['35.239.129.111']) {
                        sh 'ssh bharatbodh@35.239.129.111 "cd /home/bharatbodh/bharatbodh-bench/apps && git pull origin master"'
                    }
                }
            }
        }
        stage('Pushing Changes') {
            steps {
                script {
                    sshagent(credentials: ['35.239.129.111']) {
                        sh '''
                            ssh bharatbodh@35.239.129.111 "
                            cd /home/bharatbodh/bharatbodh-bench/apps &&
                            git add . &&
                            git commit -m 'Automated commit' &&
                            git push origin master
                            "
                        '''
                    }
                }
            }
        }
    }
}
