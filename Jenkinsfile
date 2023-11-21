pipeline {
    agent any
    environment {
        name = 'mayuri'
    }
    parameters{
            string(name:'person', defaultValue: 'Mayuri T', description: "Who are you?")
            booleanParam(name:'isMale', defaultValue: true, description: "")
            choice(name:'City', choices: ['Jaipur', 'Mumbai', 'Pune'], description: "")

    }
    stages {
        stage('Run a command') {
            steps {
               sh '''
               ls
               date
               pwd
               '''
            
            }
        }
        stage('Environment Variables') {
             environment {
             username = 'dhani'
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                echo 'Deploy on Test'
                sh 'echo "${name}"'
                sh 'echo "${person}"'
            }
        }
        stage('Continue >?') {
            input{
                message "Should we continue?"
                ok "yes, we should"
            }
            steps {
                echo 'Deploy On Prod'
            }
        }
        stage('Deploy on Prod') {
            steps {
                echo 'Deploy On Prod'
            }
        }
    }
    post{
        always { 
            echo 'I will always say Hello again!'
        }
        failure{
            echo 'Failure'
        }
        success{
            echo 'Successful'
        }
    }
}
