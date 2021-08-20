pipeline {
    agent any
    tools {maven "maven"}
    stages {
      stage('Maven clean and Install ') {
        steps {
          sh '''
          mvn clean
          mvn install
          '''     
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