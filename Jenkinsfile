pipeline {
    agent any

    stages {
 stage('Checkout') {
    steps {
        git branch: 'main', url: 'https://github.com/ondeckera1/final-k8s-project.git'
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
curl -v -u admin:password \
--upload-file target/final-webapp-0.0.1-SNAPSHOT.jar \
http://10.17.10.121:8081/repository/final/com/example/finalwebapp/0.0.1-SNAPSHOT/final-webapp-0.0.1-SNAPSHOT.jar
'''
            }
        }
    }
}

