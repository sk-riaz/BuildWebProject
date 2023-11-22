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
               deploy adapters: [tomcat9(credentialsId: '92499e17-09eb-44b0-acd4-77521463b7ed', path: '', url: 'http://54.209.250.117:9091/')], contextPath: null, war: '**/target/*.war'
            }
        }
    }
}
