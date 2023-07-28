pipeline {
    agent any

    // Declare the 'parameters' variable at the top level so it can be accessed in other stages
    def parameters = [:]

    stages {
        stage('Read Parameters') {
            steps {
                script {
                    def paramsFileContent = sh(returnStdout: true, script: 'git show origin/main:parameters.txt') // Change 'origin/master' to the appropriate branch if needed

                    paramsFileContent.split('\n').each { line ->
                        def keyValue = line.split('=')
                        def paramName = keyValue[0]
                        def paramOptions = keyValue[1].split('\\|')

                        parameters[paramName] = choice(choices: paramOptions, description: "Select your ${paramName}", name: paramName)
                    }
                }
            }
        }

        stage('Print Parameters') {
            steps {
                // Access the 'parameters' variable here to print the selected value
                script {
                    echo "Parameters selected ${params.PARAMETER}" // Replace <PARAMETER_NAME> with the actual parameter name you want to display
                }
            }
        }

        // Add more stages as needed
        // ...
    }

    // Define the properties block outside the stages to make the 'parameters' variable available to the entire pipeline
    options([
        parameters(parameters)
    ])
}
