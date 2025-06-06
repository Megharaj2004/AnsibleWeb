pipeline {
    agent any  // Use any available agent

    tools {
jdk 'jdk'
maven 'maven'
        gradle 'gradle'  // Ensure this matches the name configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Megharaj2004/AnsibleWeb.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'  // Run Maven build
            }
        }

        stage('archive'){
      steps{
        archiveArtifacts artifacts:'target/*.war', fingerprint: true
      }
    }
    stage('deploy'){
      steps{
        sh 'mvn clean package'
        sh 'sudo ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
    }
  }

        
        
       
        

        
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
