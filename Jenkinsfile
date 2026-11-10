pipeline {
    agent none

    stages {
        stage('build') {
            agent {
                label 'buildnode'
            }
            steps {
                deleteDir()

                sh '''
                    git clone https://github.com/nabeelnico008-hub/git.git              
                    ls -la
                '''

                stash name: 'webpage', includes:'git/**'
            }
        }

        stage('deploy') {
            agent {
                label 'deploynode'
            }
            steps {
                deleteDir()
                unstash 'webpage'
                sh '''
                    rm -rf /var/www/html/*
                    cp -r git/* /var/www/html/
                    ls -la /var/www/html/
                '''
            }
        }
    }
}
