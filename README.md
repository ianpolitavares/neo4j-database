# Conectando-se ao Neo4j a partir do VSCode

Este guia irá ajudá-lo a se conectar a uma instância do Neo4j a partir do Visual Studio Code (VSCode) e executar consultas Cypher.

## Pré-requisitos

1. Extensão [Neo4j Cypher Query Language Support](https://marketplace.visualstudio.com/items?itemName=neo4j-cypher-tools.neo4j-cypher) instalada no seu VSCode.
2. [Python](https://www.python.org/downloads/) instalado em seu computador.
3. Driver [Neo4j para Python](https://neo4j.com/developer/python/) instalado em seu ambiente Python. Você pode instalar o driver executando o seguinte comando no terminal:

```bash
pip install neo4j
```

## Conectando-se ao Neo4j

Para se conectar ao Neo4j, você precisa do URL de conexão, do nome de usuário e da senha da sua instância.

Exemplo de como se conectar ao Neo4j e executar uma consulta Cypher:

```python
from neo4j import GraphDatabase

uri = "neo4j://your-neo4j-instance:7687"  # mudar 
driver = GraphDatabase.driver(uri, auth=("user", "password"))  # mudar

def print_all(tx):
    result = tx.run("MATCH (n) RETURN n")
    for record in result:
        print(record)

with driver.session() as session:
    session.read_transaction(print_all)

driver.close()
```

## Extensão Neo4j para VSCode

A extensão Neo4j para VSCode. Aqui está um resumo de como instalar e usar a extensão, com base no [blog oficial do Neo4j](https://neo4j.com/developer-blog/run-cypher-without-leaving-your-ide-with-neo4j-vscode-extension/):

### Instalação e Uso

Para instalar a extensão, vá para a Visual Studio Code Marketplace e procure por "Neo4j". Clique em "Install" para instalar a extensão.

Depois de instalada, a extensão Neo4j aparecerá na barra lateral do VSCode. Você pode clicar no ícone para abrir o painel da extensão.

### Adicionando uma nova Conexão de Banco de Dados

Para adicionar uma nova conexão de banco de dados, clique no botão "Add Connection" no painel da extensão. Você será solicitado a fornecer o URL de conexão, o nome de usuário e a senha do seu banco de dados Neo4j.

Depois de adicionar a conexão, você pode clicar na conexão para se conectar ao banco de dados. Uma vez conectado, você pode ver todas as suas bases de dados no painel da extensão.

### Executando Consultas Cypher

Para executar uma consulta Cypher, primeiro abra um novo arquivo Cypher (`.cyp`) ou um arquivo existente. Você pode então escrever sua consulta no arquivo e executá-la pressionando `Ctrl+Enter` (ou `Cmd+Enter` no macOS).

A extensão irá executar a consulta no banco de dados atualmente selecionado e mostrar os resultados no painel de resultados.

## Documentação oficial

[documentação oficial do Neo4j](https://neo4j.com/docs/).
