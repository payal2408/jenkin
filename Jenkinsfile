pipeline {
    agent any

    environment {
        RAILS_ENV = 'test'
    }

    stages {
        stage('Setup Ruby') {
            steps {
                // Load RVM and use Ruby version
                sh '''
                    source $HOME/.rvm/scripts/rvm
                    rvm use 3.1.4 --install --default
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    gem install bundler
                    bundle install
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh 'bundle exec rake test' // or rspec, etc.
            }
        }
    }

    post {
        always {
            echo 'Build finished!'
        }
        success {
            echo 'All good! ✅'
        }
        failure {
            echo 'Something failed 💥'
        }
    }
}
