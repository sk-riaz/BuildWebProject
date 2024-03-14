pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo 'Archiving Artifacts'
                    archiveArtifacts artifacts:'**/target/*.war'
                }
            }

        }
        stage("Deploy into tomcat"){
            steps{
              deploy adapters: [tomcat9(credentialsId: 'e2a6ab27-9f82-4ec7-8817-77a2231e4cb5', path: '', url: 'http://13.201.54.189:8083/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
