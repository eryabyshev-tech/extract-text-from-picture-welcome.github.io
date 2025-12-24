pipeline {
  agent any

  options { timestamps() }

  stages {
   stage('Deploy (Ansible)') {
      steps {
          sh '''
            set -euo pipefail
            export ANSIBLE_HOST_KEY_CHECKING=false
            ansible-playbook -i hosts.txt deploy.yml
          '''
      }
    }
  }

  post {
    always { sh 'rm -f inventory.tmp || true' }
  }
}