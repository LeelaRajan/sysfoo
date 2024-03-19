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
                archiveArtifacts artifacts: '**/*.war', fingerprint: true
            }
        }
    }
}
