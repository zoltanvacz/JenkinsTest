pipeline{
    agent any
    
    stages{
        stage('Hello World'){
            steps{
                echo 'Hello Jenkin'
            }
		}
		stage('Verify Git Branch'){
            steps{
                echo '$GIT_BRANCH'
            }
        }
		stage('Goodbye'){
            steps{
                echo 'Goodbye'
            }
        }
    }
}