<div align="center">

# SecAuth (Projeto Sentinela)
**Enterprise Security-as-a-Service Infrastructure**

[![Status: Production MVP](https://img.shields.io/badge/Status-Production_MVP-success?style=flat-square)](#)
[![Security: AES-256-GCM](https://img.shields.io/badge/Encryption-AES--256--GCM-blue?style=flat-square)](#)
[![Security: HMAC-SHA256](https://img.shields.io/badge/Signatures-HMAC--SHA256-blue?style=flat-square)](#)

*Plataforma B2B que fornece um ecossistema completo de criptografia, licenciamento e autenticação para softwares com alto risco de engenharia reversa e pirataria.*

🔗 **Acesso ao Ambiente MVP:** [authjtkeeste1991ka.squareweb.app](https://authjtkeeste1991ka.squareweb.app)

</div>

---

## Escopo de Engenharia e Execução (Founder)

Todo o ciclo de vida desta infraestrutura foi idealizado, arquitetado e **desenvolvido 100% de forma solo**. A construção deste ecossistema exigiu a aplicação de uma engenharia de operações unificada, dividida em três pilares principais:

* **Engenharia de Software (Full-Stack):** Criação das interfaces (Painel SaaS e Admin), modelagem e desenvolvimento da API RESTful blindada, integração de gateway de pagamentos e construção dos SDKs/Client Apps.
* **DevOps e Infraestrutura:** Orquestração de servidores, deploy isolado com roteamento de redes e configuração otimizada de banco de dados em nuvem (MongoDB Atlas).
* **Pentest e Segurança Ofensiva:** Condução de testes de invasão rigorosos, auditoria de código contínua, implementação de *Rate Limiting* estrito e blindagem contra *Man-in-the-Middle*, injeções de banco de dados e engenharia reversa de pacotes.

---

## Topologia de Arquitetura (Particionamento Isolado)

Para garantir a máxima integridade, o sistema utiliza um **método de particionamento estrito**. Os módulos operam em ambientes independentes que comunicam exclusivamente através de uma API restrita:

1. **Back-End (O Cofre):** Motor isolado responsável pela validação criptográfica, persistência de dados, processamento de checkout e emissão de licenças.
2. **Front-End (Painel do Cliente):** Landing Page e Dashboard (SaaS) voltado para programadores e empresas gerenciarem seus softwares e usuários.
3. **Painel Admin (Torre de Controle):** Ambiente restrito à administração da SecAuth para auditoria, gestão financeira e acionamento de *kill-switches*.
4. **SDKs / Client Apps:** Módulos de integração injetados nos softwares terceiros (C++, Python, Node.js) para estabelecer comunicação autenticada com o servidor.

```mermaid
graph TD
    subgraph Client Environment
        SDK[Softwares Terceiros / Client SDK]
    end

    subgraph Public Network
        FRONT[Dashboard SaaS<br/>authjtkeeste1991ka.squareweb.app]
    end

    subgraph Secure Internal Network
        API((API RESTful<br/>Endpoint Core))
        DB[(MongoDB Atlas<br/>Encrypted Storage)]
        ADMIN[Admin Panel<br/>Acesso Restrito]
    end

    %% Flow Connections
    SDK == "Assinatura HMAC-SHA256 + HWID" ==> API
    FRONT <== "AES-256-GCM (Payload Criptografado)" ==> API
    API <== "Private Peering" ==> DB
    ADMIN <== "Acesso Auditado" ==> API

    classDef public fill:#f8fafc,stroke:#cbd5e1,stroke-width:1px,color:#334155;
    classDef secure fill:#f1f5f9,stroke:#94a3b8,stroke-width:1px,color:#0f172a;
    classDef core fill:#0f172a,stroke:#38bdf8,stroke-width:2px,color:#f8fafc;
    
    class FRONT,SDK public;
    class ADMIN,DB secure;
    class API core;
