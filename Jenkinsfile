pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/ondeckera1/final-k8s-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh '''
                curl -u admin:password \
                --upload-file target/final-webapp-0.0.1-SNAPSHOT.jar \
                http://nexus:8081/repository/homework6-snapshot/com/example/finalwebapp/0.0.1-SNAPSHOT/final-webapp-0.0.1-SNAPSHOT.jar
                '''
            }
        }
    }
}

