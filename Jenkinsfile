pipeline {
    agent {
        docker {
            image 'qaninja/rubywd'
        }
    }
    
    stages{
        stage('Build'){
            steps {
                echo 'Building or resolving depenencies!'
                sh 'bundle install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running regression tests'
                sh 'bundle exec cucumber -p ci'
            }
        }
        stage ('UAT'){
            steps {
                echo 'Waiting for user acceptance'
                input(message: 'Go to production?', ok: 'Yes')
            }
        }
        stage ('Prod'){
            steps {
                echo 'WebApp is ready!'
            }
        }
    }
}