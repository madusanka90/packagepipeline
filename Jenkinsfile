pipeline {
    agent any
    tools { 
        maven 'local_maven' 
        jdk 'local_java' 
    }

    stages{
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "MAVEN_HOME = ${MAVEN_HOME}"
                ''' 
            }
        }

        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving....'
                    archiveArtifacts artifacts: '**/target/*.war'
                } 
            }
        }
    }
}