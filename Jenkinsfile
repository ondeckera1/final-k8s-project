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
                curl -u admin:password \
                --upload-file target/final-webapp-0.0.1-SNAPSHOT.jar \
                http://10.17.10.121:8081/repository/homework6-snapshot/com/example/demo/0.0.1-SNAPSHOT/demo-0.0.1-SNAPSHOT.jar
                '''
            }
        }
    }
}

