// Jenkinsfile (Declarative Pipeline)
// pipeline,stages,steps == sections
// under sections we can add multiple declaratives
// echo == declaratives
pipeline {
    agent any
    
    environment{
        name = 'hitesh'
    }
    
    parameters{
        string(name: 'person', defaultValue: 'hitesh salgotra', description: 'who are you')
        
        booleanParam(name: 'Sonar_Check',
        defaultValue: false,
        description: 'Tick the box to run Sonar Check')
    booleanParam(name: 'Junit_Test_Cases',
        defaultValue: false,
        description: 'Tick the Box to run junit test cases')
        
    

    }
    
    stages {
        stage('Test pipeline as a command') {
            steps {
                // pipeline run as a command
                // here iam running 2 commands but if i want to run 2 command inside a single sh i need to use triple inverted commans
                sh 'date'
                sh 'pwd'
            }
        }
        stage('pipeline as multiple command') {
            steps {
                sh '''
                date
                ls
                pwd
                '''
            }
        }
        
        stage('Environment') {
            // the env can be global and can be initialized inside the stage.
            steps {
                sh 'echo "the bundle id is: ${BUILD_ID}"'
                sh 'echo "my name is ${name}"'
            }
        }
        
        stage('Parameters') {
            // the parameter can be global and can be initialized inside the stage.
            steps {
                sh 'echo "the bundle id is: ${BUILD_ID}"'
                sh 'echo "my name is ${person}"'
                
                sh 'echo ""'
            }
        }
        
        stage('taking input from user') {
            // this input can only be added locally inside the stage
            input{
                message "should we continue"
                ok "you can continue"
            }
            steps {
                echo 'deploying hello world'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'deploying hello world'
            }
        }
    }
        post{ 
        always { 
            echo 'I will always say Hello again!'
        }
        failure{
            echo 'i will run when any stage will fail '
        }
        success{
            echo ' i will run when whole pipeline run successfuly'
        }
      }
    }
