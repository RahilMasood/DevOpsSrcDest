pipeline {
    agent any

    tools {
        maven 'maven'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/RahilMasood/DevOpsSrcDest.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run Application') {
            steps {
                //sh 'java -jar target/MyMavenApp-1.0-SNAPSHOT.jar'
                sh 'mvn exec:java -Dexec.mainClass="com.example.App"'
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
