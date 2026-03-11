pipeline {
    agent any
    environment {
        // Memaksa Jenkins pakai socket lokal
        DOCKER_HOST = 'unix:///var/run/docker.sock'
    }
    stages {
        stage('Cek Docker') {
            steps {
                // Kita tes apakah perintah docker dasar bisa jalan
                sh 'docker version'
                sh 'docker images'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Mencoba Pull Image..." '
                sh 'docker pull shippingdocker/php-composer:7.4'
            }
        }
    }
}