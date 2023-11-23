pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C1-80276/kubernetes.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_PaLl5Fxzkq8et76Hg8CaWv9__SQ | /usr/bin/docker login -u chiraag77 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t chiraag77/chiraag_repo:mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push chiraag77/chiraag_repo:mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker make new service') {
            steps {
                sh '/usr/bin/docker service create --replicas 5 --name myservice -p 9090:80 chiraag77/chiraag_repo:mywebsite'
            }
        }
    }   
}

            
