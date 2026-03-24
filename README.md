# 🚀 Relatório Operacional de Pré-Decolagem

**Atividade Integradora – FIAP | GRUPO 404**

## 👨‍💻 Integrantes

| Nome                      | RM       |
| ------------------------- | -------- |
| Fernando dos Santos Motta | rm570046 |
| Caetano de Medeiros Bona  | rm569262 |
| Joedson da Silva Souza    | rm573981 |

## 📖 Explicação do Projeto

Este repositório contém a automação da análise de pré-decolagem de um veículo espacial, avaliando em tempo real se a nave está apta para o lançamento com base na telemetria e análise auxiliada por Inteligência Artificial.

O projeto foi dividido nos seguintes componentes principais:

- **`telemetria.md` (1.1, 1.6)**: Documento de especificação que mapeia e define as faixas seguras dos sensores do foguete (temperatura, integridade estrutural, níveis de energia e combustível, pressões e módulos críticos), contendo também a reflexão crítica.
- **`pre_decolagem.ipynb` (1.3)**: Notebook com o algoritmo principal em Python que processa a entrada de dados dos sensores e decide se o lançamento está autorizado ("PRONTO PARA DECOLAR") ou não ("DECOLAGEM ABORTADA") baseado nas faixas de segurança estabelecidas.
- **`calculo_autonomia.ipynb` (1.4)**: Notebook focado na análise energética. Realiza o cálculo da autonomia inicial da nave, cruzando a capacidade total teórica, a carga real disponível no momento, as taxas de perdas térmicas e o consumo estimado durante a ignição e ascensão principal.
- **`analise_assistida.ipynb` (1.5)**: Integração com IA. Através da API da OpenRouter consumimos um LLM (modelo `stepfun/step-3.5-flash`), enviamos os dados de telemetria base formatados, e solicitamos à IA uma classificação dinâmica dos parâmetros vitais, o levantamento de possíveis anomalias e sugestões de mitigação de riscos, gerando assim um forte parecer para o Diretor de Voo.

## 🖼️ Prints da Execução

Abaixo, encontram-se as evidências de execução com sucesso de cada script:

### Algoritmo de Verificação (`pre_decolagem.ipynb`)

![Print da Verificação Pré-Decolagem](./prints/print_execucao_pre_decolagem.png)

### Análise Energética (`calculo_autonomia.ipynb`)

![Print da Análise Energética](./prints/print_execucao_calculo_autonomia.png)

### Análise Assistida por IA (`analise_assistida.ipynb`)

![Print da Análise Assistida por IA](./prints/print_execucao_analise_assistida.png)

## ⚙️ Instruções de Execução do Código

Os códigos do projeto foram elaborados no formato _Jupyter Notebook_ (`.ipynb`). Portanto, podem ser executados localmente ou na nuvem.

### 1. Executando os Scripts (Colab recomendado):

Recomendamos vivamente utilizar o **Google Colab**, visto que o script com inteligência artificial (`analise_assistida.ipynb`) depende de uma _secret keys_ localmente inserida que gerencia o ambiente do notebook do Colab para consultar a API.

- Faça o upload dos três notebooks na sua própria conta do Colab.
- **Atenção em `analise_assistida.ipynb`**:
  1. Na barra lateral esquerda do ambiente do Colab, abra a funcionalidade chamada **"Secrets" (Segredos - ícone de Chave)**.
  2. Crie um novo registro com o exato nome `OPENROUTER_API_KEY` e cole o código (chave) da API OpenRouter gerado/fornecido.
  3. Certifique-se de habilitar e dar acesso para esse _Notebook_ àquela chave criada.
- Em cada Notebook, execute as células sequencialmente processando todas as entradas (`Ctrl+Enter` ou botão de 'Play').

### 2. Executando Localmente (IDE):

Para executar a telemetria e o cálculo energético localmente:

1. Certifique-se de ter o interpretador **Python 3.x** e o pacote Jupyter instalado.

```bash
pip install jupyter requests
```

2. Inicie a atividade usando sua IDE preferida com suporte a `.ipynb` (como o VS Code, PyCharm, etc) ou rolando no terminal com `jupyter notebook` a partir da raiz do repositório. Lembre-se de instalar as bibliotecas citadas acima.

## 🗺️ Fluxograma

Para visualizar o fluxograma do projeto, **baixe o arquivo [`fluxograma.png`](./fluxograma.png)** e abra-o diretamente no seu navegador (a renderização da imagem pode não funcionar corretamente ao visualizar pelo GitHub).
