pipeline {
    agent any
    tools {maven "maven"}
    stages {
      /*
      stage('Maven Build ') {
        steps {
          sh '''
          ./mvnw clean
          ./mvnw install
          '''     
        }
      } */

      stage ('Upload file') {
            steps {
                rtUpload (
                    serverId: artifactory-server,
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "target/spring-petclinic-rest-2.4.2.jar",
                                        "target": "Spring-Petclinic-Rest-Local"
                                    }
                                ]
                            }"""
                )
            }
        }

/*
      stage('Approval') {
        steps {
          script {
            def userInput = input(id: 'confirm', message: 'Apply Terraform?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Apply terraform', name: 'confirm'] ])
          }
        }
      }
*/
      
    }
}