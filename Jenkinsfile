pipeline {
    agent any // Executa a pipeline em qualquer agente disponível

    environment {
        // Defina as variáveis de ambiente necessárias para os testes, se houver
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm // Faz o checkout do código-fonte do repositório Git
            }
        }
        
        stage('Restore Dependencies') {
            steps {
                script {
                    // Restaura as dependências do projeto .NET
                    bat 'dotnet restore' // Use 'bat' no Windows
                    // sh 'dotnet restore' // Use 'sh' em ambientes Unix
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // Compila o projeto .NET
                    bat 'dotnet build --no-restore' // Use 'bat' no Windows
                    // sh 'dotnet build --no-restore' // Use 'sh' em ambientes Unix
                }
            }
        }
        
        stage('Run Tests') {
            steps {
                script {
                    // Executa o programa de testes .NET
                    // Certifique-se de substituir 'path/to/your/test/project' pelo caminho correto do seu projeto de teste
                    bat 'dotnet run --project API/API.csproj' // Use 'bat' no Windows
                    // sh 'dotnet run --project path/to/your/test/project' // Use 'sh' em ambientes Unix
                }
            }
        }
    }
    
    post {
        // As ações aqui são executadas após a conclusão das etapas de pipeline
        always {
            echo 'A pipeline foi concluída.'
        }
        success {
            echo 'Todos os testes foram executados com sucesso!'
        }
        failure {
            echo 'Falha ao executar os testes. Verifique os logs para mais detalhes.'
        }
    }
}
