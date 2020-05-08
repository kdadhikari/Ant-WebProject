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
    }
}
