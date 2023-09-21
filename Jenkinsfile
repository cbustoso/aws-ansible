pipeline {
    agent any
    parameters {
        choice(name: 'ServerName', choices: ["Server1"], description: 'Selecciona Servidor')
    }
    stages {
        stage('Ansible-Playbook Execution') {
            steps {
                echo 'Executing Ansible Playbook'
                ansiblePlaybook colorized: true, credentialsId: 'ansible_user_auth', installation: 'Default', inventory: 'inventory/inventory.yml',extras: '-e host_group=\"${ServerName}\"', playbook: 'playbook/install_nginx_pb.yaml'
            }
        }
    }
}