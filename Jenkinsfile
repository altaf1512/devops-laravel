node {
    // Memaksa Jenkins bicara lewat socket, bukan lewat network/HTTPS
    withEnv(['DOCKER_HOST=unix:///var/run/docker.sock']) {
        
        stage('Checkout') {
            checkout scm
        }

        stage('Build') {
            // Kita panggil Docker secara manual agar lebih stabil
            sh "docker pull shippingdocker/php-composer:7.4"
            sh "docker run --rm -v /var/run/docker.sock:/var/run/docker.sock shippingdocker/php-composer:7.4 php -v"
            sh 'echo "Build Sederhana Berhasil!"'
        }

        stage('Testing') {
            sh 'echo "Menjalankan Test..."'
            sh 'docker run --rm ubuntu echo "Test Passed!"'
        }

        stage('Deploy') {
            sh 'echo "Simulasi Deploy Berhasil!"'
        }
    }
}