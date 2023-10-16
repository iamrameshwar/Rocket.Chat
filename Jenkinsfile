pipeline {
    agent any

    stages {
       stage("Build") {
            steps {
              def composeFile = 'docker-compose-local.yml'
                sh "sudo docker compose -f ${composeFile}  down --remove-orphans"
                sh "sudo docker container prune --force"
                sh "sudo docker image prune --force"
            }
        }
        stage("Deploy") {
            steps {
                def composeFile = 'docker-compose-local.yml'
                sh "sudo docker compose -f ${composeFile} up --build --no-deps --renew-anon-volumes --detach --remove-orphans"
            }
        }
    }
}
