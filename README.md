# 🤖 Assistente Analítico Corporativo com IA (LangChain & Llama 3)

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white" alt="Jupyter">
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge" alt="LangChain">
  <img src="https://img.shields.io/badge/Llama_3-0466C8?style=for-the-badge" alt="Llama 3">
  <img src="https://img.shields.io/badge/Groq-API-FF4B4B?style=for-the-badge" alt="Groq">
</p>

> **Status:** Concluído (Fase 1 - PoC) ✔️ <br>
> **Estudo de Caso:** [Leia o artigo completo no LinkedIn](https://www.linkedin.com/pulse/construindo-um-assistente-virtual-corporativo-com-llama-thiago-farias-u3jvf/)

## 📝 1. Contexto e Problema de Negócio
No ecossistema corporativo atual, analistas e gestores gastam horas procurando informações específicas dentro de relatórios em PDF, degravações de reuniões ou sites corporativos extensos . O desafio é extrair inteligência dessas bases não estruturadas de forma rápida, sem correr o risco de a IA inventar informações (as famosas "alucinações").

## 🎯 2. Objetivo
Desenvolver um Assistente Virtual analítico construído no ecossistema LangChain que extrai texto de múltiplas fontes e responde a perguntas em linguagem natural . O diferencial crítico desta solução é a aplicação de governança informacional: a ferramenta blinda as respostas baseando-se exclusivamente no contexto fornecido, eliminando o risco de alucinações .

## 🗂️ 3. Fonte de Dados (Ingestão)
O assistente possui suporte integrado para leitura híbrida das seguintes fontes não estruturadas :
*   Páginas Web (Sites corporativos e artigos) .
*   Documentos corporativos locais (PDFs densos) .
*   Transcrições automáticas de vídeos do YouTube (Reuniões e Apresentações) .

## 🛠️ 4. Tecnologias e Ferramentas
- **Linguagem e Ambiente:** Python, Jupyter Notebook / Google Colab .
- **Orquestração de IA:** LangChain (`langchain-community`) .
- **Modelo de Linguagem (LLM):** Llama 3.3 (70B Versatile) .
- **Infraestrutura de Inferência:** Groq API (Processamento de alta velocidade) .

## ⚙️ 5. Arquitetura e Engenharia de Contexto

O projeto "Asimo" prioriza a flexibilidade de leitura e a baixa latência de resposta, operando através das seguintes lógicas :

- **Ingestão Híbrida e Loaders:** Utilização nativa do LangChain (`WebBaseLoader`, `PyPDFLoader`, e `YoutubeLoader`) para converter múltiplos formatos brutos em texto puro .
- **Injeção Direta de Contexto (Context Stuffing):** Aproveitamento da ampla janela de contexto do modelo, compilando o conteúdo total extraído e injetando-o dinamicamente no `ChatPromptTemplate` do assistente analítico .
- **Memória Conversacional Acumulativa:** Para garantir que o bot mantenha o raciocínio em perguntas encadeadas e análises complexas, o script mantém o histórico contínuo da sessão iterando uma lista de mensagens entre `user` e `assistant` .
- **Alta Performance de Inferência:** Graças à utilização do LLM Llama 3 instanciado através da infraestrutura da Groq API, as respostas investigativas são geradas praticamente em tempo real .

## 🚀 6. Guia de Reprodução do Projeto

O projeto atualmente está estruturado em um ambiente interativo (Jupyter Notebook / Google Colab) para facilitar testes rápidos e validação do fluxo .

**Passo a passo para execução:**
1. Clone o repositório e certifique-se de possuir uma chave de API gratuita gerada no [Console da Groq](https://console.groq.com/) .
2. No seu ambiente virtual, instale as dependências executando: 
   `pip install langchain==0.3.0 langchain-groq==0.2.0 langchain-community==0.3.0 youtube_transcript_api==0.6.2 pypdf==5.0.0` .
3. Execute as células do Notebook sequencialmente. O módulo `getpass` solicitará sua chave da Groq API de forma segura (sem salvar no código-fonte) .
4. Um menu interativo será exibido no terminal de saída :
   - Digite `1` para analisar URL de Sites .
   - Digite `2` para analisar Documentos PDF locais (inserir o arquivo `documento_analise.pdf` no diretório) .
   - Digite `3` para analisar URLs de Vídeos do YouTube .
5. Após a ingestão, faça suas perguntas analíticas. Digite `x` para encerrar o loop conversacional .
