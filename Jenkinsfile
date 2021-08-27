pipeline{
    agent any
    tools{
        maven 'Maven_home'
    }
    stages{
        stage('Checkout SCM'){
            steps{
                git url: 'https://github.com/kaushik12499/Jenkins_Spring.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn -f ./pom.xml clean install package'
                sh 'docker-compose build'
                sh 'docker-compose up'
            }
            post{
                success{
                    archiveArtifacts(artifacts: 'target/*.war', allowEmptyArchive: true)
                }
            }
        }
    }
}

