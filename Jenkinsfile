node {
    docker.image('maven:3.9.0-eclipse-temurin-11').inside('-p 3000:3000') {
        stage('Build') {
            checkout scm
            sh 'mvn -B -DskipTests clean package'
        }
        stage('Test') {
            checkout scm
            sh 'mvn test'
            junit 'target/surefire-reports/*.xml'
        }
        stage('Manual Approval') { 
            checkout scm
            input message: 'Lanjutkan ke tahap Deploy?'
        }
        stage('Deploy') { 
            checkout scm
            sh './jenkins/scripts/deliver.sh'
            sleep(time: 1, unit: 'MINUTES')
        }
    }
}