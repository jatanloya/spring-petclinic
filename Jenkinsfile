pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './mvnw package'
            }
        }
        //Stage to deploy jar file using Ansible
        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i hosts deploy.yml'
            }
        }
    }



    post {
        always {
            archiveArtifacts artifacts: '**/*.jar'
        }
    }

}
node {
  stage('SCM') {
    checkout scm
  }
}