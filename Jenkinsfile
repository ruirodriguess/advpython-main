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
                stage('Requisitos')
        {
            steps
            {
                bat 'C:/Users/ruiro/AppData/Local/Programs/Python/Python311/Scripts/pip.exe install -r requirements.txt'
            }
        }
        stage('Run')
        {
            steps
            {
                bat 'python "militar_app/app.py"'
            }
        }
        stage('Executar Testes')
        {
            steps
            {
                bat 'python "militar_app/teste.py"'
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