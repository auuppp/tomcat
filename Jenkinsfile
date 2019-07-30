pipeline {
    agent { label 'jnlp-agent' } 
    environment {
  giturl = "http://172.16.134.56:8888/root/testdocker.git"
}
    stages {
        stage('pull') { 
            steps {
                git credentialsId: '843f5002-0bc0-4e10-a078-b75411de4121', url: "${giturl}"
            }
        }
        stage('Build') { 
            steps {
                sh "docker build -t sample:v1 ."
                sh "docker tag  sample:v1 172.16.193.103/jenkins/sample:v1"
                //sh "docker login -u guoyp -p guoyp123 http://172.30.120.161"
                // 该步骤通常不应该在您的脚本中使用。请参考帮助查看详情。
                withDockerRegistry(credentialsId: 'fc3763b1-c100-4b49-b899-e5d7abfc5ed1', url: 'http://172.16.193.103/v2') {
                // some bloc
                }
                sh "docker push 172.16.193.103/jenkins/sample:v1"
                // 
            }
        }
        stage('deploy') { 
            steps {
                input id: '666666', message: 'are you ok', ok: '确认', parameters: [choice(choices: ['dev', 'test', 'online'], description: '', name: '环境')], submitter: 'admin'
                sh "kubectl create -f tomcat7.yaml"
                // 
            }
        }
    }
}