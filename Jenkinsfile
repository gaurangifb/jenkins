pipeline {
    agent any
    environment {
        name = 'gaurav'
    }
    parameters {
        string(name: 'person', defaultValue: 'Saurav Sharma', description: "Who are you?")
        booleanParam(name: 'isMale', defaultValue: true, description: "")
        choice(name: 'City', choices: ['Jaipur', 'Mumbai', 'Pune'], description: "")
    }
    stages {
        stage('Run A command') {
            steps {
                bat '''
                dir
                date /t
                cd
                '''
            }
        }
        stage('Environment Variables') {
            environment {
                username = 'myusername'
            }
            steps {
                echo "BUILD_ID: %BUILD_ID%"
                echo "Name: %name%"
                echo "Username: %username%"
            }
        }
        stage('Parameters') {
            steps {
                echo 'Deploy on test'
                echo "Name: %name%"
                echo "Person: %person%"
            }
        }
        stage('Continue ?') {
            input {
                message "Should we continue?"
                ok "Yes, we should"
            }

            steps {
                echo 'Deploy on prod'
            }
        }
        stage('Deploy on prod') {
            steps {
                echo 'Deploy on prod'
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again!'
        }
        failure {
            echo 'Failure'
        }
        success {
            echo 'Success'
        }
    }
}
