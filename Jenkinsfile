pipeline {
    agent any
    tools {maven "maven"}
    stages {
      stage('Maven Build ') {
        steps {
          sh '''
          ./mvnw clean
          ./mvnw install
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