pipeline{
    agent any
    stages{
        stage('Docker Build'){
            steps{
                bat ' docker build -t webapp .'
            }
        }
        stage('Docker login'){
            steps{
                bat 'docker login -u rohinigarlapati -p Potatotabla1.'
        }
        }
        stage('Push to docker hub'){
        steps{
            bat 'docker tag webapp rohinigarlapati/kuberdemoapp:v1'
            bat 'docker push rohinigarlapati/kuberdemoapp:v1'
        }
        }
        stage('Deploy to kubernetes'){
            steps{
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
    post{
        success{
            echo 'Pipeline succesfull'
        }
        failure{
            echo 'Pipeline failure'
        }
    }



}



