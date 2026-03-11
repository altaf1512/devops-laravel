node {
    withEnv(['DOCKER_HOST=unix:///var/run/docker.sock']) { 
        checkout scm
        
        stage("Build") {
            docker.image('shippingdocker/php-composer:7.4').inside('-u root') {
                sh 'ls -la'
                sh 'echo "Simulasi Build Berhasil"'
            }
        }
        
        stage("Testing") {
            docker.image('ubuntu').inside('-u root') {
                sh 'echo "Ini adalah test"'
            }
        }

        stage("Deploy") {
            docker.image('agung3wi/alpine-rsync:1.1').inside('-u root') {
                sshagent (credentials: ['ssh-prod']) {
                    sh 'mkdir -p ~/.ssh'
                    sh 'echo "Simulasi Deploy ke \$PROD_HOST Berhasil"'
                }
            }
        }
    }
}