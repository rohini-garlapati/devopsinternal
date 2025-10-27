pipeline{
    agent any
    stages{
        stage{
            steps{
                bat ' docker build -t webapp .'
            }
        }
        stage{
            steps{
                bat 'docker login -u rohinigarlapati -p Potatotabla1.'
        }
        }
        stage{
        steps{
            bat 'docker tag webapp rohinigarlapati/kuberdemoapp:v1'
            bat 'docker push rohinigarlapati/kuberdemoapp:v1'
        }
        }
        stage{
            steps{
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
    post{
        success{
            'Pipeline succesfull'
        }
        failure{
            'Pipeline failure'
        }
    }



}
