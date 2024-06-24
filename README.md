# Desafio Flask API no Ambiente Colab

Este repositório contém a solução para o desafio de criar uma API utilizando Flask no ambiente Colab, que retorna dados de uma planilha em formato JSON.

## Instruções para Executar a API

1. Clone este repositório:
   
   git clone https://github.com/seu-usuario/Desafio_Flask_API.git
   cd Desafio_Flask_API

2. Instale as dependências:

   pip install flask flask-ngrok pandas

3. Execute o notebook Jupyter (Desafio_Flask_API.ipynb) ou execute o script Python (caso esteja disponível).

## Descrição do Desafio

O desafio consistia em criar uma API utilizando Flask no ambiente Colab que lê dados de uma planilha e retorna esses dados em formato JSON.
Endpoints

    /: Rota principal que retorna "Hello, World!".
    /data: Rota que retorna os dados da planilha em formato JSON.

Exemplo de Dados JSON Retornados

[
    {"Number": 1, "Name": "Mahesh", "Age": 25, "City": "Bangalore", "Country": "India"},
    {"Number": 2, "Name": "Alex", "Age": 26, "City": "London", "Country": "UK"},
    {"Number": 3, "Name": "David", "Age": 27, "City": "San Francisco", "Country": "USA"},
    {"Number": 4, "Name": "John", "Age": 28, "City": "Toronto", "Country": "Canada"},
    {"Number": 5, "Name": "Chris", "Age": 29, "City": "Paris", "Country": "France"}
]

## Autenticação com ngrok

Para expor a API publicamente, foi utilizado o ngrok para criar um túnel HTTP.
Configuração do ngrok

    1. Crie uma conta em ngrok.com.
    2. Obtenha seu token de autenticação no painel de controle do ngrok.
    3. Configure o token no ambiente Colab:
        !ngrok authtoken YOUR_AUTHTOKEN
## Execução

Execute a aplicação Flask com ngrok para expor a API publicamente:
from flask import Flask, jsonify
from pyngrok import ngrok
import pandas as pd

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello, World!"

@app.route("/data")
def get_data():
    data = [
        {"Number": 1, "Name": "Mahesh", "Age": 25, "City": "Bangalore", "Country": "India"},
        {"Number": 2, "Name": "Alex", "Age": 26, "City": "London", "Country": "UK"},
        {"Number": 3, "Name": "David", "Age": 27, "City": "San Francisco", "Country": "USA"},
        {"Number": 4, "Name": "John", "Age": 28, "City": "Toronto", "Country": "Canada"},
        {"Number": 5, "Name": "Chris", "Age": 29, "City": "Paris", "Country": "France"}
    ]
    return jsonify(data)

if __name__ == "__main__":
    public_url = ngrok.connect(5000)
    print(" * ngrok URL:", public_url)
    app.run()

## Conclusão

Este projeto demonstra como criar e expor uma API Flask utilizando o ambiente Colab e ngrok. Sinta-se à vontade para clonar e modificar o projeto conforme necessário.

