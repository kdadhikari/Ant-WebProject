pipeline
{
    agent any
    stages
    {
        stage ('scm checkout')
        {
            steps 
            {
                git branch: 'master', url: 'https://github.com/kdadhikari/Ant-WebProject'
            }
        }
        stage ('create working dir')
        {
            steps 
            {
                withAnt(installation: 'localant', jdk: 'localjdk-8') 
                {
                    sh 'ant prepare'
                }                
            }
        }
        stage ('compile the code')
        {
            steps 
            {
                withAnt(installation: 'localant', jdk: 'localjdk-8') 
                {
                    sh 'ant compile'
                }                
            }
        }
        stage ('create a war file')
        {
            steps 
            {
                withAnt(installation: 'localant', jdk: 'localjdk-8') 
                {
                    sh 'ant war'
                }                
            }
        } 
        stage ('creat a ear file')
        {
            steps 
            {
                withAnt(installation: 'localant', jdk: 'localjdk-8') 
                {
                    sh 'ant ear'
                }                
            }
        }
        stage ('deploy the project')
        {
            steps
            {
                sshagent(['deploytomcat'])
                {
                    sh 'scp -o StrictHostKeyChecking=no */war/*.war ec2-user@172.31.20.127:/var/lib/tomcat/webapps
                }
            }
        }

    }
}
