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
                sh 'cd /home/ubuntu/spring-petclinic'
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