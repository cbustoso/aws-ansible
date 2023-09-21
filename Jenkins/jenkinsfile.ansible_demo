pipeline {
    agent any
    parameters {
        choice(name: 'TagKey', choices: ["Environment"], description: 'Choose tag')
        choice(name: 'TagValue', choices: ["Dev"], description: 'Choose tag')
    }
    stages {
        stage('Ansible-Playbook Execution') {
            steps {
                echo 'Executing Ansible Playbook'
                ansiblePlaybook colorized: true, credentialsId: 'ansible_user_auth', installation: 'Default', inventory: 'inventory/dynamic.aws_ec2.yml',extras: '-e host_group=\"tag_${TagKey}_${TagValue}\"', playbook: 'playbook/ansible-demo-pb.yaml'
            }
        }
    }
}