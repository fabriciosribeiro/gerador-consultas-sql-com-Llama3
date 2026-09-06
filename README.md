# SQL Natural

Projeto para conversão de perguntas formuladas em linguagem natural em consultas SQL.

## Status

Em desenvolvimento.

Esta versão corresponde à etapa preliminar do projeto, dedicada à preparação do ambiente e ao carregamento local de um modelo Llama 3.1 8B em formato quantizado. A implementação da preparação dos dados, do ajuste do modelo e da interface de consulta será incorporada nas próximas versões.

## Objetivo

Desenvolver uma solução capaz de interpretar solicitações em linguagem natural e produzir consultas SQL correspondentes, reduzindo a necessidade de conhecimento avançado de SQL para consultas sobre bases de dados relacionais.

A proposta considera execução local do modelo, evitando o envio das informações consultadas para serviços externos.

## Tecnologias

- Python
- Llama 3.1 8B
- Unsloth
- PyTorch
- Hugging Face Transformers
- TRL
- PEFT
- bitsandbytes
- xformers

## Modelo

A etapa atual utiliza o modelo:

`unsloth/Meta-Llama-3.1-8B`

O carregamento é realizado com quantização em 4 bits para reduzir o consumo de memória durante a execução.

## Estrutura

```text
sql-natural/
├── sql-natural.ipynb
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
```

## Requisitos

A etapa atual foi preparada para execução em ambiente com GPU compatível com o carregamento do modelo quantizado.

Recomenda-se utilizar um ambiente virtual ou uma sessão isolada para instalar as dependências.

## Instalação

Clone o repositório:

```bash
git clone URL_DO_SEU_REPOSITORIO
cd sql-natural
```

Crie um ambiente virtual:

```bash
python -m venv .venv
```

Ative o ambiente no Linux:

```bash
source .venv/bin/activate
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

## Execução

Abra o notebook:

```text
sql-natural.ipynb
```

Execute as células na ordem apresentada.

A etapa preliminar realiza:

1. instalação das dependências necessárias;
2. importação dos componentes do Unsloth;
3. definição do modelo;
4. carregamento do Llama 3.1 8B com quantização em 4 bits.

## Próximas etapas

- preparação do conjunto de dados;
- definição do formato de treinamento;
- ajuste do modelo para geração de SQL;
- avaliação das consultas produzidas;
- criação de uma interface para entrada de perguntas;
- integração com uma base de dados de demonstração;
- documentação dos resultados e limitações.

## Licença

Este projeto está disponível sob a licença MIT.
