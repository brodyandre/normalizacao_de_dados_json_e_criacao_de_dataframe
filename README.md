# Normalização de Dados JSON com Pandas

Este projeto demonstra como normalizar dados JSON com a biblioteca **Pandas** e fazer o processamento de dados aninhados de uma API externa. O código realiza a obtenção, normalização e mesclagem de dados de uma API, transformando-os em um formato tabular para fácil manipulação e análise.

## 📦 Requisitos

Antes de executar o código, certifique-se de ter os seguintes pacotes instalados:

- `pandas`
- `requests`

Você pode instalar as dependências com o seguinte comando:

```bash
pip install pandas requests

🛠️ Como Executar o Código
Clone este repositório ou baixe o código para o seu computador.

Execute o código em um ambiente Python. Se estiver utilizando um Jupyter Notebook ou Google Colab, basta copiar e colar o código na célula de execução.

📜 Explicação do Código
O código é composto pelas seguintes etapas:

1. Obtenção dos Dados JSON
O código faz uma requisição HTTP para a API https://jsonplaceholder.typicode.com/users, que retorna uma lista de objetos JSON.


import requests

url = 'https://jsonplaceholder.typicode.com/users'
response = requests.get(url)

2. Criação do DataFrame
Usamos pandas para criar um DataFrame a partir dos dados JSON obtidos.

import pandas as pd

df = pd.DataFrame(data)

3. Normalização das Colunas Aninhadas
A normalização é feita para as colunas address e company, que são dicionários aninhados.

address_df = pd.json_normalize(df['address'])
company_df = pd.json_normalize(df['company'])

4. Renomeação das Colunas Normalizadas
Para evitar conflitos de nomes ao mesclar os DataFrames, as colunas são renomeadas com prefixos.

5. Mesclagem dos DataFrames
Os DataFrames normalizados são concatenados ao DataFrame principal.

df = pd.concat([df, address_df, company_df], axis=1)

6. Remoção das Colunas Originais Aninhadas
As colunas address e company são removidas do DataFrame original.

df = df.drop(columns=['address', 'company'])

7. Exibição do DataFrame Final
O DataFrame final, agora com dados normalizados, é exibido.

print(df.head())

📊 Saída Esperada
Após a execução do código, o DataFrame final exibirá as seguintes colunas:

| id  | name          | username | email                                         | phone                 | website       | address\_street | address\_suite | address\_city | address\_zipcode | address\_geo\_lat | address\_geo\_lng | company\_name   | company\_catchPhrase                   | company\_bs                 |
| --- | ------------- | -------- | --------------------------------------------- | --------------------- | ------------- | --------------- | -------------- | ------------- | ---------------- | ----------------- | ----------------- | --------------- | -------------------------------------- | --------------------------- |
| 1   | Leanne Graham | Bret     | [Sincere@april.biz](mailto:Sincere@april.biz) | 1-770-736-8031 x56442 | hildegard.org | Kulas Light     | Apt. 556       | Gwenborough   | 92998-3874       | -37.3159          | 81.1496           | Romaguera-Crona | Multi-layered client-server neural-net | harness real-time e-markets |
| ... | ...           | ...      | ...                                           | ...                   | ...           | ...             | ...            | ...           | ...              | ...               | ...               | ...             | ...                                    |                             |

🚧 Problemas Conhecidos e Soluções
Erro: "No such file or directory"
Certifique-se de que a URL da API está correta e acessível.

Erro ao normalizar colunas aninhadas
Verifique a estrutura dos dados JSON para garantir que as colunas address e company sejam dicionários.

📝 Conclusão
Este código facilita a normalização de dados JSON aninhados, transformando-os em um formato tabular que pode ser facilmente analisado e manipulado. Isso é útil para processar dados de APIs externas ou qualquer outra fonte que forneça dados em formato JSON com estrutura complexa.

📄 Licença
Este projeto é licenciado sob a licença MIT - consulte o arquivo LICENSE para mais detalhes.

💬 Contato
Autor: Luiz André de Souza

GitHub: brodyandre

Email: luiz.andre@example.com
