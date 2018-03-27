pipeline {
    parameters{
        string(name: 'tomcat_dev', defaultValue: '127.0.0.1:9080', description: 'Staging Server')

    }
    triggers{
        pollSCM('* * * * *')
    }

    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts: '**/target/*.war'
                }
            }
        }
        stage('Sanity check'){
            steps{
                input "Esi mi dobar?"
            }
        }
        stage('Deploy to staging'){
            steps{
                sh "cp **/target.war /home/petar/Documents/apache-tomcat-8.5.29-staging/webapps"
            }

        }

    }
}
