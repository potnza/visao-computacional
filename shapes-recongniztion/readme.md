Projeto de Detecção de Formas

Pré-requisitos Certifique-se de que você tenha o Python instalado em seu sistema. Este projeto foi desenvolvido com Python 3.

Criar e Ativar um Ambiente Virtual python -m venv venv

Ativar o Ambiente Virtual:

No Windows (Prompt de Comando ou PowerShell): .\venv\Scripts\activate

Se você encontrar um erro relacionado à execução de scripts, execute o seguinte comando no PowerShell para permitir a execução de scripts: Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process

Instalar Dependências pip install opencv-python matplotlib

Executar o Programa Para rodar o programa de detecção de formas:

Coloque a imagem que deseja analisar no mesmo diretório do script ou forneça o caminho correto no código, precisamente na linha 60 "main('shapes.jpg')"

Autor: Lucas Potenza