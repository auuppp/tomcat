pipeline {
    agent { label 'jnlp-agent' } 
    environment {
<<<<<<< HEAD
  giturl = "http://172.16.134.56:8090/root/testdocker.git"
=======
  giturl = "http://172.16.134.56:8888/root/testdocker.git"
>>>>>>> a3a7fb7df3b109c4085e0ed63805ca095662efd0
}
    stages {
        stage('pull') { 
            steps {
<<<<<<< HEAD
                //git credentialsId: 'cf91ae3a-2a64-446f-93d9-5f952e8f5d23', url: "${giturl}"
=======
                git credentialsId: 'cf91ae3a-2a64-446f-93d9-5f952e8f5d23', url: "${giturl}"
>>>>>>> a3a7fb7df3b109c4085e0ed63805ca095662efd0
                // 
            }
        }
        stage('Build') { 
            steps {
                sh "docker build -t sample:v1 ."
                sh "docker tag  sample:v1 test1test2/sample:v1"
                sh "docker login -u test1test2 -p 1234567890 https://index.docker.io/v1/"
                sh "docker push test1test2/sample:v1"
                // 
            }
        }
        stage('deploy') { 
            steps {
                sh "kubectl create -f tomcat7.yaml"
                // 
            }
        }
    }
}