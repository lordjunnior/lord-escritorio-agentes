<p align="center">
  <img src="client/public/favicon.svg" alt="Lord Escritório de Agentes Logo" width="80" height="80" />
</p>

<h1 align="center">Lord Escritório de Agentes</h1>

<p align="center">
  <strong>Escritório virtual em pixel art para observabilidade e controle de agentes de IA locais, com aceleração por GPU e custo zero.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-ativo-success.svg" alt="Status" />
  <img src="https://img.shields.io/badge/execu%C3%A7%C3%A3o-100%25%20local-blue.svg" alt="Execução Local" />
  <img src="https://img.shields.io/badge/custo-zero%20APIs-green.svg" alt="Custo Zero" />
  <img src="https://img.shields.io/badge/acelera%C3%A7%C3%A3o-GPU%20VRAM-orange.svg" alt="Aceleração GPU" />
  <img src="https://img.shields.io/badge/licen%C3%A7a-MIT-lightgrey.svg" alt="Licença MIT" />
</p>

---

## Visão Geral

O **Lord Escritório de Agentes** transforma logs estáticos e sessões de terminal em um ambiente visual interativo em pixel art. Cada projeto aberto torna-se uma sala dedicada e cada agente ou subagente torna-se um personagem animado que reflete suas ações em tempo real.

Diferente de soluções convencionais dependentes de serviços proprietários na nuvem, esta versão foi adaptada para operar com soberania total:
* **Zero Custo de Operação:** Sem faturas de API ou limites arbitrários de tokens por hora.
* **Privacidade Absoluta:** O servidor opera isolado em loopback (`127.0.0.1`). Nenhuma informação de código, arquivo ou histórico sai da sua máquina.
* **Aceleração Local por GPU:** Projetado para integrar perfeitamente com modelos de código executados na sua placa de vídeo (como Qwen 2.5 Coder 7B/14B).

---

## Como Funciona a Observabilidade

O sistema atua como um leitor de eventos passivo:

1. **Ciclo de Vida das Salas:** Ao iniciar uma tarefa, a sala do projeto é mobiliada e a luz é acesa. Quando o trabalho termina e a sessão é encerrada, o agente apaga a luz, desce pelo elevador e o espaço é convertido em jardim.
2. **Ações em Tempo Real:** 
   * **Trabalhando:** O avatar senta na mesa e digita enquanto gera código ou analisa arquivos.
   * **Execução Longa:** Quando roda comandos pesados (builds, testes), o agente aguarda na mesa com animações contextuais.
   * **Pedidos de Permissão:** Quando um comando exige autorização no terminal, o agente levanta a mão com um alerta piscante, permitindo aprovação visual.
   * **Subagentes:** Auxiliares sobem pelo elevador com crachás de identificação e entregam pacotes de resultado ao agente principal antes de partir.
   * **Tempo Ocioso:** Em momentos sem tarefas, os avatares circulam pelas áreas comuns (copa, banheiros e lounge).

---

## Requisitos do Sistema

* **Sistema Operacional:** Windows 10/11, Linux ou macOS.
* **Ambiente de Execução:** Node.js 22.12+ (recomendado Node 24) e npm.
* **Hardware para IA Local:** Placa de vídeo com 8GB a 12GB+ de VRAM para carregamento dos modelos de código quantizados.
* **Servidor de Inferência Local:** Qualquer ferramenta compatível com a API OpenAI (porta local `11434` ou `8000`), como Ollama, LM Studio ou vLLM.

---

## Guia de Instalação e Execução

### 1. Clonar e Instalar Dependências

No terminal da pasta do projeto:

```bash
git clone [https://github.com/lordjunnior/lord-escritorio-agentes.git](https://github.com/lordjunnior/lord-escritorio-agentes.git)
cd lord-escritorio-agentes
npm install
2. Iniciar o Escritório Virtual
Para modo de desenvolvimento com hot-reload:

Bash
npm run dev
Para compilação de produção e inicialização rápida:

Bash
npm run build
npm start
Abra no navegador: http://localhost:4747

Conectando Agentes Locais na GPU (Custo Zero)
Para direcionar o cérebro dos agentes para a sua GPU sem gastar créditos externos, aponte a CLI do Codex para a sua porta de inferência local antes de iniciar as sessões:

No Windows (PowerShell):
PowerShell
# Aponta a API para a sua porta local (exemplo: Ollama ou LM Studio)
$env:OPENAI_BASE_URL="[http://127.0.0.1:11434/v1](http://127.0.0.1:11434/v1)"
$env:OPENAI_API_KEY="local"

# Define o modelo focado em programação carregado na sua VRAM
$env:CODEX_MODEL="qwen2.5-coder:7b"
No Linux / macOS (Bash/Zsh):
Bash
export OPENAI_BASE_URL="[http://127.0.0.1:11434/v1](http://127.0.0.1:11434/v1)"
export OPENAI_API_KEY="local"
export CODEX_MODEL="qwen2.5-coder:7b"
Com essas variáveis ativas, qualquer execução via terminal processa os comandos diretamente na sua GPU. O Lord Escritório de Agentes detecta automaticamente os arquivos de sessão gerados em disco e renderiza todo o fluxo em pixel art.

Estrutura do Repositório
Plaintext
lord-escritorio-agentes/
├── client/         # Interface web em pixel art (Vite + TypeScript)
├── server/         # Servidor passivo local (zero dependências de runtime)
│   ├── accounts/   # Detecção e mapeamento de contas e diretórios
│   ├── sources/    # Observadores de arquivos de sessão e hooks (Codex/Claude)
│   ├── model/      # Máquina de estados das salas, mesas e personagens
│   └── config.ts   # Configurações do servidor e travas de segurança
├── scripts/        # Scripts de automação, hooks e empacotamento
└── package.json    # Manifest do projeto e comandos de build
Privacidade e Segurança
Isolamento de Rede: Por padrão, o servidor responde exclusivamente em 127.0.0.1.

Zero Telemetria: Acesso externo ao Habblaud World desativado por padrão no código-fonte.

Integridade: Não armazena nem manipula chaves de autenticação de terceiros.