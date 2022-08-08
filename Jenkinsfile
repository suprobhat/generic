pipeline {
    agent any
    environment {
        IS_AUTO_TRIGGERED = false;
        userInput = null;
        target_dir= null;
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    if (env.myParameter != null) {
                        echo 'Automatic build triggered'
                        IS_AUTO_TRIGGERED = true;
                    } else {
                        echo 'Manual build triggered'
                        timeout(time: 2, unit: 'MINUTES') {
                            myParameter = input(id: 'userInput'
                            , message: 'Set the message to print:'
                            , parameters: [
                            [$class: 'TextParameterDefinition'
                            , defaultValue: 'No entry'
                            , description: 'Manual execution detected'
                            , name: 'myParameter']])
                        }
                        IS_AUTO_TRIGGERED = false;
                    }
 
                    echo 'hello pipeline: ' + myParameter + " auto triggered?: " + IS_AUTO_TRIGGERED;
 
                    if(myParameter == ''){
                        currentBuild.result = 'FAILURE'
                        error "Invalid branch name, end of pipeline"
                    }
                    else{
                        git branch: myParameter, credentialsId: 'jaehoo',
                        url: 'https://github.com/suprobhat/generic.git'
                    }
 
                }
            }
        }
    }
}
