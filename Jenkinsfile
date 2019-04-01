pipeline {
    agent none

    stages {
        stage('Build') {
            agent { docker { image 'maven:3-alpine' } }
            steps {
                sh 'mvn -B -DskipTests clean package'
                stash includes: '**/target/*.jar', name: 'app'
            }
        }
        stage('Deliver') {
            agent { label 'ubuntu_18' }
            steps {
                unstash 'app'
                sh './jenkins/scripts/deliver.sh'
                sh './jenkins/scripts/deliver.sh'
                sh './jenkins/scripts/deliver.sh'
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
