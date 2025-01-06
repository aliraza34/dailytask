pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aliraza34/dailytask.git'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Testing HTML file'
            }
        }
        stage('Deploy') {
            steps {
                sshPublisher(publishers: [
                    sshPublisherDesc(
                        configName: 'UbuntuServer',
                        transfers: [
                            sshTransfer(
                                sourceFiles: '**/*.html',
                                remoteDirectory: '/var/www/html',
                                execCommand: 'sudo systemctl restart nginx'
                            )
                        ]
                    )
                ])
            }
        }
    }
}

