# Data Warehouse e Análise de Dados COVID

![GitHub repo size](https://img.shields.io/github/repo-size/leticiatavaresds/DW-COVID?color=a21360&style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/leticiatavaresds/DW-COVID?color=a21360&style=for-the-badge)
![Made With](https://img.shields.io/badge/Made%20With-Python-lightgrey?color=a21360&style=for-the-badge)
![GitHub repo file count](https://img.shields.io/github/directory-file-count/leticiatavaresds/DW-COVID?color=a21360&style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/leticiatavaresds/DW-COVID?color=a21360&style=for-the-badge)

# Introdução

O escopo do projeto é dividido em três partes. Primeiramente, é construído um Data Warehouse seguido de uma modelagem dimensional estrela com 
os microdados da COVID em Minas Gerais. A partir de consultas ao Data Warehouse elaborado, é então realizada uma Análise 
Exploratória para por fim construir um modelo de aprendizagem de máquina com a finalidade de predizer o desempenho de um aluno com base em informações preenchidas 
nas provas como dados da instituição, características e perfil socioeconômico do aluno. As bases de dados importadas possuem 169 variáveis, mas no presente projeto 
algumas foram descartadas. 

# Índice

- [Introdução](#introdução)
- [Microdados COVID - MG ](#microdados-covid---mg)
  - [Obtenção dos Dados](#obtenção-dos-dados)
  - [Tratamento de Dados](#tratamento-de-dados)
- [Análise Exploratória](#análise-exploratória)
- [Modelo de Predição](#modelo-de-predição)
- [Execução](#execução)
- [Licença](#licença)


# Microdados COVID - MG 

O primeiro dataset usado foi obtido no portal de Dados Abertos da Secretaria de Estado de Saúde de Minas Gerais, 
disponibilizado no formato CSV desde 02/06/2021. A descrição detalhada do conjunto de dados pode ser consultada no Dicionário de Dados. 
Foram utilizadas as tabelas 'Sistemas' e 'Laboratórios'. Ambas descrevem, para cada linha da tabela, uma descrição de um paciente de SARS-Cov 2 
do estado de Minas Gerais. A primeira contém dados extraídos das plataformas oficiais do governo SIVEP_Gripe, Esus-ve e REDCAP, coletados diariamente, 
exceto nos finais de semana. Já a segunda tem os dados extraídos de banco de dados laboratoriais públicos, privados e de rede de farmácias. 
Foram coletados também dados referentes a estimativa de população divididas da seguinte forma: População Brasileira > População por Região > População por Estado. 
E por último dados referentes ao PIB das regiões, este com muito mais detalhes de dados, mas o interesse é fazer o cruzamento com as informações que temos nos dados
de estimativa de população. Os dois últimos dados foram obtidos do site do IBGE.

[⬆ Voltar ao topo](#data-warehouse-e-análise-de-dados-covid)<br>

## Obtenção dos Dados

O notebook “00_Download_Dados.ipynb”, implementado na linguagem python, primeiramente cria a pasta “Microdados_Covid”, caso não exista,  no mesmo diretório em que 
o script se encontra. Em seguida, realiza o download dos arquivos e os salva nesta pasta, sendo os microdados de Covid e os dados da população por município.

O notebook “01_Criação_Banco_de_Dados”, refere-se, pasmem, a criação do banco de dados. O primeiro passo dessa etapa foi descompactar os arquivos, 
para isso contamos com a biblioteca ZipFile e o Pandas para preparar os dados. 


## Tratamento de Dados

Após feita a conexão com o banco de dados, antes da armazenagem no banco, foi realizado um trabalho de Data Wrangling, 
começando com remoção de algumas colunas, pois não seriam utilizadas. Da remoção de nulos, optamos pela estratégia de eliminar as linhas com nulos. 
Renomeamos também algumas colunas com o objetivo de melhor identificar as variáveis. A última etapa antes da criação das nossas dimensões para a armazenagem no 
banco foi a de corrigir alguns tipos de valores como Idade e ID.

[⬆ Voltar ao topo](#data-warehouse-e-análise-de-dados-covid)<br>

# Modelagem Dimensional 

O modelo apresenta a tabela fato sem fato, além de 4 tabelas dimensões.

[⬆ Voltar ao topo](#data-warehouse-e-análise-de-dados-covid)<br>

# Execução

Os Scripts devem ser executados na seguinte ordem:
- 00_Download_Dados.ipynb
- 01_Criação_Banco_de_Dados.ipynb
- 02_Analise_Exploratória_Dados.ipynb
- 03_Aprendizado_Random_Forest_Nota.ipynb

[⬆ Voltar ao topo](#data-warehouse-e-análise-de-dados-covid)<br>

# Licença

The MIT License (MIT) 2022 - Letícia Tavares. Leia o arquivo [LICENSE.md](https://github.com/leticiatavaresds/DW-COVID/blob/master/LICENSE.md) para mais detalhes.

[⬆ Voltar ao topo](#data-warehouse-e-análise-de-dados-covid)<br>
