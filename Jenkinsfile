pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
               sh 'mvn clean package'
            }
        }
        stage('Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.war'
            }
        }
        stage('tomcat server deployment') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'admindemo', path: '', url: 'http://localhost:8081/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
