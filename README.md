# 🤖 Assistente Corporativo IA: Ingestão Multi-Formato com Llama 3 & Groq

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge" alt="LangChain">
  <img src="https://img.shields.io/badge/Llama_3-0466C8?style=for-the-badge" alt="Llama 3">
  <img src="https://img.shields.io/badge/Groq-API-FF4B4B?style=for-the-badge" alt="Groq">
</p>

> **Problema de Negócio:** Analistas e gestores gastam horas procurando informações específicas dentro de relatórios em PDF, degravações de reuniões ou sites corporativos extensos.
>
> **A Solução:** Um Assistente Virtual construído no ecossistema LangChain que extrai texto de múltiplas fontes e responde a perguntas em linguagem natural. A ferramenta blinda as respostas baseando-se **exclusivamente** no contexto fornecido, eliminando o risco de alucinações.

---

## ⚙️ Arquitetura e Funcionalidades

O projeto "Asimo" foi desenvolvido como uma Prova de Conceito (PoC) analítica, priorizando flexibilidade de leitura e baixa latência de resposta:

*   **Ingestão de Dados Híbrida:** Suporte integrado via LangChain (`langchain-community`) para leitura de Páginas Web (`WebBaseLoader`), documentos corporativos (`PyPDFLoader`) e transcrições de vídeos (`YoutubeLoader`).
*   **Injeção Direta de Contexto:** Aproveitamento da ampla janela de contexto do modelo (Context Stuffing), compilando o conteúdo total extraído e injetando-o dinamicamente no `ChatPromptTemplate` do assistente.
*   **Memória Conversacional Acumulativa:** O script mantém o histórico contínuo da sessão iterando uma lista de mensagens entre `user` e `assistant`, garantindo que o bot mantenha o raciocínio em perguntas encadeadas.
*   **Alta Performance de Inferência:** Utilização do modelo **Llama 3.3 (70B Versatile)** instanciado através da infraestrutura de alta velocidade da **Groq API**, gerando respostas praticamente em tempo real.

## 🚀 Guia de Execução

O projeto atualmente está estruturado em um ambiente interativo (Jupyter Notebook / Google Colab) para facilitar testes rápidos e visualização do fluxo.

### 1. Pré-requisitos
Certifique-se de ter uma chave de API gratuita gerada no [Console da Groq](https://console.groq.com/).

### 2. Instalação das Dependências
No seu ambiente virtual Python, ou na primeira célula do seu Notebook, instale as bibliotecas necessárias:

```bash
pip install langchain==0.3.0 langchain-groq==0.2.0 langchain-community==0.3.0 youtube_transcript_api==0.6.2 pypdf==5.0.0

```

### 3. Configuração e Uso

1. Execute as células do Notebook sequencialmente.
2. A biblioteca `getpass` solicitará sua chave da Groq API de forma segura (a chave não ficará salva no código-fonte).
3. O menu interativo será exibido no terminal de saída:
* Digite `1` para URL de Sites.
* Digite `2` para Documentos PDF locais (insira o arquivo `documento_analise.pdf` no mesmo diretório).
* Digite `3` para URL de Vídeos do YouTube.


4. Após o carregamento, digite suas perguntas. Para encerrar o assistente, digite `x`.

---

## 🛣️ Próximos Passos (Roadmap de Evolução)

Como este projeto nasceu como uma PoC analítica, as seguintes melhorias de Engenharia de Software estão planejadas para a versão de produção:

* [ ] **Migração para Arquitetura RAG:** Substituir a injeção direta de texto por um processo de *Chunking*, *Embeddings* e um Banco de Dados Vetorial (como ChromaDB ou FAISS) para suportar PDFs de milhares de páginas sem estourar o limite de *tokens*.
* [ ] **Refatoração Modular:** Converter o fluxo do Jupyter Notebook em scripts modulares `.py` (ex: `loaders.py`, `chatbot.py`, `main.py`).
* [ ] **Gestão de Variáveis de Ambiente:** Substituir o uso do `getpass` pela biblioteca `python-dotenv` e um arquivo `.env` dedicado.
* [ ] **Interface Gráfica:** Envolver a lógica do backend em um Web App utilizando **Streamlit**.

---

**Autor:** [Thiago Farias Lourenço](https://www.linkedin.com/in/thiagofarias1908/)
