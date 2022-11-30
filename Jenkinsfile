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
		        sh 'sudo apt-get install ansible'
                sh '/var/jenkins_home/script.sh'
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