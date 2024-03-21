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
                deploy adapters: tomcat8(url:"http://localhost:8081/", credentialsId: "admin"), war: 'target/sysfoo.war', contextPath: '/app'
            }
        }
    }
}
