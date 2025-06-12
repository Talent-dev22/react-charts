pipeline{
    agent any

    stages{
        stage("verification"){
            steps{
                sh 'helm -version'
                if [ $? == 0]
                  echo "Helm installed"
                else
                  echo "Helm is not installed. kindly check and install it"
                  exit(1)
            }
        }
        stage("helm deploy"){
            steps{
                sh 'helm upgrade --install javaspring $WORKSPACE'
            }
        }

    }
    post {
        always{
            emailext body: '''Hi,

     The jenkins has been failed . please check it.

     Thanks
     Devops Team''', subject: 'testing jenkins pipeline: $JOB_URL', to: 'malleshdevops2021@outlook.com'
        }
    }
}

