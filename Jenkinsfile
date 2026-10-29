
pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage('Build') {
            steps {
                dir('student-management') {
                    sh 'mvn -B clean compile'
                }
            }
        }

        stage('Tests') {
            steps {
                dir('student-management') {
                    sh 'mvn -B test'
                }
            }
        }

        stage('Package') {
            steps {
                dir('student-management') {
                    sh 'mvn -B package -DskipTests'
                }
            }
        }
    }



post {
    always {
        junit testResults: 'student-management/target/surefire-reports/*.xml',
              allowEmptyResults: true
    }
    success {
        echo 'Pipeline execute avec succes !'
    }
    failure {
        echo 'Echec du pipeline : verifier la console.'
    }


    }
}
