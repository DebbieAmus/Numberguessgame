pipeline {
    agent any
    environment {
        MVN_HOME = '/path/to/maven' // Update this to your Maven installation path
        JAVA_HOME = '/path/to/java' // Update this to your Java installation path
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/your-username/NumberGuessGame.git'
            }
        }
        stage('Build') {
            steps {
                sh "${MVN_HOME}/bin/mvn clean package"
            }
        }
        stage('Test') {
            steps {
                sh "${MVN_HOME}/bin/mvn test"
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://your-tomcat-server:8080')],
                contextPath: 'NumberGuessGame', war: '**/target/*.war'
            }
        }
    }
}
