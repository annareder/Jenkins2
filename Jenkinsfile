pipeline {
  agent any
  stages {
    stage('Clone devops') {
      steps {
        sh "rm -Rf /var/lib/jenkins/workspace/gpipeline/code"
        sh "mkdir /var/lib/jenkins/workspace/gpipeline/code"
        sh "git clone https://github.com/annareder/Jenkins.git /var/lib/jenkins/workspace/gpipeline/code -b devops"
      }
    }

    stage('Clone main') {
      steps {
        sh "rm -Rf /var/lib/jenkins/workspace/gpipeline/site"
        sh "mkdir /var/lib/jenkins/workspace/gpipeline/site"
        sh "git clone https://github.com/annareder/Jenkins.git /var/lib/jenkins/workspace/gpipeline/site -b main"
      }
    }

    stage('Deploy main to 20.18.12.180') {
      steps {
        sh "echo 20.18.12.180 > /var/lib/jenkins/workspace/gpipeline/code/hosts"
        sh "ansible-playbook /var/lib/jenkins/workspace/gpipeline/code/playbook.yml -u root --key-file=/key/id_rsa -i /var/lib/jenkins/workspace/gpipeline/code/hosts"
      }
    }

    stage('Clone dev') {
      steps {
        sh "rm -Rf /var/lib/jenkins/workspace/gpipeline/site"
        sh "mkdir /var/lib/jenkins/workspace/gpipeline/site"
        sh "git clone https://github.com/annareder/Jenkins.git /var/lib/jenkins/workspace/gpipeline/site -b dev"
      }
    }

    stage('Deploy dev to 20.89.23.89') {
      steps {
        sh "echo 20.89.23.89 > /var/lib/jenkins/workspace/gpipeline/code/hosts"
        sh "ansible-playbook /var/lib/jenkins/workspace/gpipeline/code/playbook.yml -u root --key-file=/key/id_rsa -i /var/lib/jenkins/workspace/gpipeline/code/hosts"
      }
    }

    stage('Clone feature') {
      steps {
        sh "rm -Rf /var/lib/jenkins/workspace/gpipeline/site"
        sh "mkdir /var/lib/jenkins/workspace/gpipeline/site"
        sh "git clone https://github.com/annareder/Jenkins.git /var/lib/jenkins/workspace/gpipeline/site -b feature"
      }
    }

    stage('Deploy feature to 20.210.204.79') {
      steps {
        sh "echo 20.210.204.79 > /var/lib/jenkins/workspace/gpipeline/code/hosts"
        sh "ansible-playbook /var/lib/jenkins/workspace/gpipeline/code/playbook.yml -u root --key-file=/key/id_rsa -i /var/lib/jenkins/workspace/gpipeline/code/hosts"
      }
    }
  }
}
