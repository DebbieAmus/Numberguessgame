pipeline {
    agent any
    triggers {
        githubPush() // Triggers a build when code is pushed to GitHub
    }
    environment {
        MVN_HOME = '/usr/share/maven/bin/mvn' // Update this to your Maven installation path
        JAVA_HOME = '/usr/lib/jvm/java-17-amazon-corretto.x86_64' // Update this to your Java installation path
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'Dev', url: 'https://github.com/DebbieAmus/Numberguessgame.git'
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
      
    }
}
