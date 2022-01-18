pipeline {
    agent any

    stages {

        stage('Quality Check') {
            steps {
                echo 'Sonar Quality Check'
                 sh 'mvn clean install sonar:sonar -DskipTests=true -Dsonar.sources=src/main -Dsonar.tests=src/test -Dsonar.projectKey=abc12345test -Dsonar.projectName=SimpleApplication -Dsonar.projectVersion=1.0 -Dsonar.login=admin -Dsonar.password=test -Dsonar.java.binaries=target/classes -Dsonar.java.test.binaries=target/test-classes'  
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'mvn package'
            }
        }

    }

    post {
        always {
            junit 'target/surefire-reports/**/*.xml'
        }
    }

}