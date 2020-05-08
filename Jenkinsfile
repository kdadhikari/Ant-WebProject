pipeline
{
    agent any
    stages
    {
        stage
        {
            steps ('scm checkout')
            {
                git branch: 'master', url: 'https://github.com/kdadhikari/Ant-WebProject'
            }
        }
        stage
        {
            steps ('create working dir')
            {
                withAnt(installation: 'localant', jdk: 'localjdk-8') 
                {
                    sh 'ant prepare'
                }                
            }
        }
    }

}
