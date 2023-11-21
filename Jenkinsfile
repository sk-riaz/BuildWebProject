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
               deploy adapters: [tomcat9(credentialsId: 'cd83419f-abba-4130-8bdd-18da6a7024f2', path: '', url: 'http://34.206.53.194:8081/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
