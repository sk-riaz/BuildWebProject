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
               deploy adapters: [tomcat9(credentialsId: '3c8329fd-88c1-4c40-9c59-18cdb85ffa1a', path: '', url: 'http://44.213.99.42:8082/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
