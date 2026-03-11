node {
    checkout scm
    
    // Kita panggil Docker dengan socket langsung di argumen .inside
    stage("Build") {
        docker.image('shippingdocker/php-composer:7.4').inside('-u root -v /var/run/docker.sock:/var/run/docker.sock') {
            sh 'ls -la'
            sh 'echo "Simulasi Build Berhasil"'
        }
    }
    
    stage("Testing") {
        docker.image('ubuntu').inside('-u root -v /var/run/docker.sock:/var/run/docker.sock') {
            sh 'echo "Ini adalah test"'
        }
    }

    stage("Deploy") {
        docker.image('agung3wi/alpine-rsync:1.1').inside('-u root -v /var/run/docker.sock:/var/run/docker.sock') {
            sshagent (credentials: ['ssh-prod']) {
                sh 'mkdir -p ~/.ssh'
                sh 'echo "Simulasi Deploy Berhasil"'
            }
        }
    }
}