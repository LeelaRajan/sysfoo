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
        stage('Expose with Ngrok') {
            steps {
                script {
                    sh 'ngrok http 8080' // Replace 8080 with the port of your localhost web service
                }
            }
        }
    }
}
