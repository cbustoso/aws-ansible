pipeline {
    agent any
    stages {
        stage('Ansible-Playbook Execution') {
            steps {
                script {
                    try {
                        // Copia los archivos de inventario y playbooks de aws-ansible a la instancia EC2
                        sshagent(credentials: ['705fa984-d6b9-408c-9acd-f1d0289bb09f']) {
                            sh "scp -o StrictHostKeyChecking=no -r inventory playbook ubuntu@eec2-44-201-84-56.compute-1.amazonaws.com:/tmp/"
                        }
                        
                        // Ejecuta el playbook de Ansible en la instancia EC2
                        sshagent(credentials: ['705fa984-d6b9-408c-9acd-f1d0289bb09f']) {
                            sh "ssh -o StrictHostKeyChecking=no ubuntu@ec2-44-201-84-56.compute-1.amazonaws.com 'cd /tmp/playbook && ansible-playbook -i /tmp/inventory/inventory.yml nginx_install.yml'"
                        }
                    } catch (Exception e) {
                        currentBuild.result = 'FAILURE'
                        error("Error during Ansible playbook execution: ${e.message}")
                    }
                }
            }
        }
    }
}