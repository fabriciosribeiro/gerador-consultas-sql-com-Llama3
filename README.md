# Gerador de Consultas SQL com Llama 3.1

Projeto de fine-tuning de um modelo de linguagem para geração de consultas SQL a partir de perguntas formuladas em linguagem natural.

O objetivo é explorar a aplicação de modelos de linguagem abertos em uma tarefa de **Text-to-SQL**, utilizando o Llama 3.1 8B e técnicas de ajuste fino para adaptar o modelo ao domínio de geração de consultas SQL.

## Sobre o projeto

A proposta é permitir que uma pessoa formule uma pergunta em linguagem natural, como:

> Quais pessoas têm mais de 56 anos?

e que o modelo seja capaz de produzir uma consulta SQL correspondente, considerando o contexto fornecido.

O projeto utiliza um modelo de linguagem aberto como ponto de partida e realiza um processo de fine-tuning utilizando um conjunto de exemplos contendo contexto, pergunta e resposta esperada.

Além do treinamento e da inferência no ambiente de desenvolvimento, o modelo resultante foi disponibilizado no Hugging Face e também preparado para utilização local em formato GGUF.

## Modelo

O projeto utiliza como modelo-base o:

**Llama 3.1 8B**

O modelo treinado neste projeto está disponível no Hugging Face:

**[fabricioribeiro/llama-3.1-8B-texto-para-sql](https://huggingface.co/fabricioribeiro/llama-3.1-8B-texto-para-sql)**

A versão quantizada em formato GGUF pode ser utilizada localmente com o Ollama.

## Tecnologias utilizadas

* Python
* Llama 3.1 8B
* Hugging Face Transformers
* Unsloth
* PyTorch
* TRL
* PEFT
* bitsandbytes
* xformers
* Google Colab
* Ollama
* GGUF

## Fine-tuning

O treinamento utiliza o modelo Llama 3.1 8B carregado com quantização em 4 bits, reduzindo o consumo de memória durante o processo.

Os exemplos utilizados no treinamento são organizados a partir de três informações principais:

* **Contexto:** informações sobre a estrutura ou domínio dos dados;
* **Pergunta:** solicitação formulada em linguagem natural;
* **Resposta:** consulta SQL esperada.

Essas informações são transformadas em um formato de prompt utilizado durante o treinamento.

De forma simplificada:

```text
Contexto + Pergunta → Consulta SQL
```

O processo de fine-tuning busca adaptar o comportamento do modelo para essa tarefa específica.

## Estrutura do projeto

```text
gerador-consultas-sql-com-Llama3/
│
├── Aula_1_Finetuning_de_LLMs_abertas.ipynb
├── Finetuning_de_LLMs_abertas.ipynb
├── sql-natural.ipynb
├── requirements.txt
├── README.md
└── LICENSE
```

### Notebook principal

O arquivo utilizado como principal referência para o desenvolvimento atual é:

[`Finetuning_de_LLMs_abertas.ipynb`](./Finetuning_de_LLMs_abertas.ipynb)

Ele reúne as etapas relacionadas ao carregamento do modelo, preparação dos dados, configuração do treinamento e utilização do modelo.

Os demais notebooks representam etapas anteriores ou materiais utilizados durante o desenvolvimento do projeto.

## Execução

### 1. Clonar o repositório

```bash
git clone https://github.com/fabriciosribeiro/gerador-consultas-sql-com-Llama3.git
cd gerador-consultas-sql-com-Llama3
```

### 2. Criar um ambiente virtual

```bash
python3 -m venv .venv
```

### 3. Ativar o ambiente virtual

No Linux:

```bash
source .venv/bin/activate
```

### 4. Instalar as dependências

```bash
pip install -r requirements.txt
```

### 5. Executar o notebook

O treinamento e as etapas de experimentação podem ser executados a partir do notebook:

```text
Finetuning_de_LLMs_abertas.ipynb
```

O notebook foi desenvolvido para utilização em ambiente com suporte a GPU compatível com o processo de treinamento do modelo.

## Utilização do modelo com Ollama

Uma versão quantizada do modelo foi disponibilizada em formato GGUF para utilização local.

Com o Ollama instalado, o modelo pode ser executado utilizando:

```bash
ollama run hf.co/fabricioribeiro/llama-3.1-8B-texto-para-sql:Q4_K_M
```

Depois de carregado, é possível fornecer perguntas em linguagem natural para testar a geração de consultas SQL.

Exemplo:

```text
Liste todas as pessoas com idade superior a 56 anos.
```

O modelo deve utilizar o conhecimento adquirido durante o fine-tuning para produzir uma consulta SQL correspondente ao contexto apresentado.

## Hugging Face

O modelo treinado está disponível em:

https://huggingface.co/fabricioribeiro/llama-3.1-8B-texto-para-sql

A publicação do modelo permite que o resultado do treinamento seja reutilizado e testado fora do ambiente original de desenvolvimento.

## Objetivos de aprendizagem

Este projeto foi desenvolvido também como estudo prático dos principais componentes envolvidos no desenvolvimento e adaptação de aplicações baseadas em LLMs:

* utilização de modelos de linguagem abertos;
* carregamento de modelos com quantização;
* preparação de conjuntos de dados para fine-tuning;
* construção de prompts para tarefas específicas;
* fine-tuning de modelos de linguagem;
* utilização de Unsloth;
* utilização de Transformers e TRL;
* utilização de PEFT;
* geração de consultas SQL a partir de linguagem natural;
* publicação de modelos no Hugging Face;
* conversão e utilização de modelos em formato GGUF;
* execução local de LLMs utilizando Ollama.

## Limitações atuais

O projeto ainda está em desenvolvimento.

Entre os pontos que podem ser aprimorados estão:

* avaliação quantitativa da qualidade das consultas SQL;
* criação de um conjunto de testes independente;
* comparação entre o modelo-base e o modelo após fine-tuning;
* avaliação da execução das consultas geradas;
* tratamento de diferentes estruturas de banco de dados;
* melhoria da consistência das respostas;
* criação de uma interface para interação com o modelo;
* integração com um banco de dados de demonstração;
* documentação de exemplos de entrada e saída;
* análise de desempenho e consumo de recursos durante a inferência.

Os resultados de desempenho do modelo não são apresentados neste README enquanto não houver uma avaliação sistemática que permita medi-los de forma adequada.

## Próximos passos

As próximas etapas previstas para o projeto incluem:

* aprimorar o conjunto de dados;
* revisar o formato dos prompts;
* realizar novos experimentos de fine-tuning;
* criar uma avaliação específica para Text-to-SQL;
* testar diferentes estratégias de inferência;
* disponibilizar uma interface para consulta;
* integrar o modelo a uma base de dados de demonstração;
* documentar exemplos de consultas geradas;
* avaliar a utilização do modelo em ambiente local.

## Licença

Este projeto está disponível sob a licença MIT.

Consulte o arquivo [`LICENSE`](./LICENSE) para obter os detalhes da licença.
