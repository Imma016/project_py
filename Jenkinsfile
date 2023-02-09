pipeline {
    agent any

    stages {
        stage('checkout code from git') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'imma', url: 'https://github.com/Imma016/project_py.git']])
            }
        }
        stage('deploy ansible') {
            steps {
                echo 'running playbook'
                ansiblePlaybook becomeUser: 'ubuntu', inventory:'host.ini', playbook: 'flask-playbook.yml'
            }
        }
    }
}
