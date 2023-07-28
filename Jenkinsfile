pipeline {
    agent any

    stages {
        stage('Read Parameters') {
            steps {
                script {
                    def paramsFileContent = sh(returnStdout: true, script: 'git show origin/main:parameters.txt') // Change 'origin/master' to the appropriate branch if needed

                    def parameters = [:]

                    paramsFileContent.split('\n').each { line ->
                        def keyValue = line.split('=')
                        def paramName = keyValue[0]
                        def paramOptions = keyValue[1].split('\\|')

                        parameters[paramName] = choice(choices: paramOptions, description: "Select your ${paramName}", name: paramName)
                    }

                    properties([
                        parameters(parameters)
                    ])
                }
            }
        }

        stage('Print Parameters') {
		steps{
			echo "Parameters selected ${params.paramName}"
		}
	}
    }
}
