node {
    docker.image('maven:3.9.0-eclipse-temurin-11').inside('-p 3000:3000') {
        stage('Build') {
            checkout scm
            sh 'mvn -B -DskipTests clean package'
        }
    }
}