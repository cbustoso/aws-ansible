pipeline {
    agent any
    parameters {
        choice(name: 'ServerGroups', choices: ["webservers"], description: 'Selecciona un grupo')
    }
    stages {
        stage('Ansible-Playbook Execution') {
            steps {
                echo 'Executing Ansible Playbook'
                ansiblePlaybook colorized: true, credentialsId: 'ansible_user_auth', installation: 'Default', inventory: 'inventory/inventory.yml',extras: '-e host_group=\"${ServerGroups}\"', playbook: 'playbook/install_nginx_pb.yaml'
            }
        }
    }
}