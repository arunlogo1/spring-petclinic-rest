pipeline {
    agent any
    tools {maven "maven"}
    stages {
      
      stage('Maven Build') {
        steps {
          sh '''
          ./mvnw clean
          ./mvnw install
          '''     
        }
      } 

      stage ('Renaming the Artifact Version') {
            steps {
                dir('target') {
                sh '''
                filename=`echo *.jar | awk -F '.jar' '{print $1}'`
                fileout="${filename}-${BUILD_NUMBER}.jar"
                mv *.jar fileout
                '''
                }
            }
        }

      stage ('Upload file') {
            steps {
                rtUpload (
                    serverId: "artifactory-server",
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "target/*.jar",
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