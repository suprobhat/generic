pipeline {
    agent any
    environment {
        IS_AUTO_TRIGGERED = true;
        userInput = null;
        target_dir= null;
    }
    stages {
        stage('Checkout') {
           steps {
              script {
                 echo 'hello pipeline: '+ env.myParameter
              }
          }
        }
    }
}
