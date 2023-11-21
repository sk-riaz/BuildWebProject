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
                deploy adapters: [tomcat9(credentialsId: '9f0377f8-6b6f-41b6-b251-2272d79480d9', path: '', url: 'http://3.237.205.12:8081/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}