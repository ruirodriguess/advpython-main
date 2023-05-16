pipeline
{
    agent any
    stages
    {
        stage('Limpar recursos')
        {
            steps
            {
                cleanWs()
            }
        }
        stage('Git')
        {
            steps
            {
               git branch: 'master', url: 'https://github.com/ruirodriguess/advpython-main'
            }
        }
        stage('Run')
        {
            steps
            {
                bat 'python "advpython-main/webserviceclient.py"'
            }
        }
        stage('Executar Testes')
        {
            steps
            {
                bat 'python "advpython-main/testing.py"'
            }
        }
        stage('Publicar Testes')
        {
            steps
            {
                junit skipOldReports: true, testResults: '**/relatorio-testes/*.xml'
            }
        }
        
    }
}