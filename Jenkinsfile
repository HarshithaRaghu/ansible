pipeline {
    agent any 
    environment {                                       // Declaring at pipeline will allow all the stages to access this variable
        SSH_CRED = credentials('SSH_CRED') 
    }
    

        stage('Performing a Dry-Run') {                 // Just for demo purpose we have hardcoded env and component; That can still be parameterised.
            when { branch pattern: "PR-.*", comparator: "REGEXP"}
            steps {
                sh "env"
                sh "Runs only aginst a PR"
                sh "ansible-playbook robot-dryrun.yml -e COMPONENT=mongodb -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW} -e ENV=dev"
            }
        }

        