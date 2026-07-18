# 🤖 Assistente Virtual IA: Análise de Dados com Llama 3

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge" alt="LangChain">
  <img src="https://img.shields.io/badge/Llama_3-0466C8?style=for-the-badge" alt="Llama 3">
</p>

## 📌 Sobre o Projeto
Este projeto foi desenvolvido para automatizar a extração e análise de informações a partir de dados não estruturados. O objetivo é demonstrar a criação de um Assistente Virtual robusto (apelidado de Asimo) capaz de ler sites, documentos em PDF e degravações de vídeos do YouTube, permitindo que o usuário faça perguntas complexas em linguagem natural e receba respostas precisas embasadas exclusivamente no contexto fornecido.

## ⚙️ Funcionalidades e Arquitetura
A aplicação foi estruturada para oferecer flexibilidade na ingestão de dados e uma interface de terminal amigável:
- **Ingestão Multi-formato:** Módulos de extração de texto para Páginas Web (URLs), arquivos PDF e vídeos do YouTube (via transcrição de áudio).
- **Memória Conversacional:** O bot mantém o histórico completo da conversa (alternando entre usuário e assistente), permitindo perguntas de acompanhamento e raciocínio contínuo sobre o documento.
- **Engenharia de Prompt (Persona):** Utilização de `ChatPromptTemplate` para blindar as respostas do modelo, garantindo que a IA não invente informações (alucinações) e baseie suas respostas estritamente no material carregado.

## 🛠️ Tecnologias Utilizadas
- **Linguagem e Ambiente:** Desenvolvido em **Python** utilizando **Jupyter Notebook / Google Colab**.
- **Orquestração de IA:** Framework **LangChain** para integração de componentes de LLM e carregamento de documentos (`WebBaseLoader`, `PyPDFLoader`, `YoutubeLoader`).
- **Modelo de Linguagem (LLM):** LLama 3.3 (70B Versatile) da Meta, acessado através da **Groq API** para inferência de altíssima velocidade.

## 🚀 Como executar o projeto localmente
Caso queira rodar a aplicação na sua máquina, siga os passos abaixo:

1. Clone este repositório:
```bash
git clone https://github.com/ThiagoFarias1908/ai-corporate-chatbot.git

```

2. Instale as dependências essenciais:

```bash
pip install langchain langchain-groq beautifulsoup4 pypdf youtube-transcript-api

```

3. Configure a sua chave da Groq API:
Ao executar o script, o terminal solicitará sua chave de forma segura utilizando a biblioteca `getpass`. Certifique-se de ter gerado uma API Key gratuita no [Console da Groq](https://console.groq.com/).
4. Execute o notebook (`.ipynb`) ou o script Python correspondente e escolha a opção de ingestão de dados no menu interativo (1 - Site, 2 - PDF, 3 - YouTube).

---

*Desenvolvido como projeto prático focado em Inteligência Artificial Generativa e Automação de Processos.*

