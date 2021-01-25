node('master') {
    stage('checkout') {
        cleanWs()
        checkout scm
    }
    stage('test') {
        withMaven(jdk: 'jdk 8u221', maven: 'maven 3.6.3') {
            sh 'mvn clean test'
        }
        allure includeProperties: false, jdk: 'jdk 8u221', results: [[path: 'allure-results']]
    }
    stage('build') {
        withMaven(jdk: 'jdk 8u221', maven: 'maven 3.6.3') {
            sh 'mvn clean install'
        }
    }
}
