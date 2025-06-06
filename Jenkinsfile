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

        stage('Test') {
            steps {
                sh 'mvn test'  // Run unit tests
            }
        }

        
        
       
        stage('Run Application') {
            steps {
                // Start the JAR application
                sh 'mvn exec:java -Dexec.mainClass=com.example.App'

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
