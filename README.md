<div align="center">

# SecAuth (Projeto Sentinela)
**Enterprise Security-as-a-Service Infrastructure**

[![Status: Production MVP](https://img.shields.io/badge/Status-Production_MVP-success?style=flat-square)](#)
[![Security: AES-256-GCM](https://img.shields.io/badge/Encryption-AES--256--GCM-blue?style=flat-square)](#)
[![Security: HMAC-SHA256](https://img.shields.io/badge/Signatures-HMAC--SHA256-blue?style=flat-square)](#)

*Plataforma B2B que fornece um ecossistema completo de criptografia, licenciamento e autenticação para softwares operando sob alto risco de engenharia reversa e pirataria.*

**Acesso ao Ambiente MVP:** [authjtkeeste1991ka.squareweb.app](https://authjtkeeste1991ka.squareweb.app)

</div>

---

## Engenharia e Arquitetura (Desenvolvimento Solo)

A arquitetura de proteção de todo o ecossistema foi desenhada e executada 100% por mim, estruturada rigorosamente para atender às exigências de segurança de alto nível do cliente. A condução do projeto abrangeu a engenharia unificada de ponta a ponta:

* **Software Engineering (Full-Stack):** Desenvolvimento integral da API RESTful, construção das interfaces web (SaaS e Admin) e integração de módulos SDK (C++, Python, Node.js) para comunicação segura com os softwares finais.
* **Cyber Security & Pentesting:** Modelagem de ameaças e blindagem ativa. Execução de testes de intrusão, proteção contra ataques Man-in-the-Middle (MitM), higienização de injeções de banco de dados e mitigação de Brute-force.
* **DevOps & Infraestrutura:** Orquestração de rotas, deploy de alta disponibilidade e configuração otimizada de banco de dados em nuvem sob regras de particionamento e Whitelisting.

---

## Topologia de Rede e Particionamento Isolado

Para garantir a máxima integridade e anular riscos de comprometimento cruzado, o sistema utiliza um método de particionamento estrito. Os módulos operam em ambientes fisicamente isolados, comunicando-se unicamente através de conexões encriptadas:

1. **Core API (Back-End):** Motor de validação criptográfica, responsável por transações de base de dados, segurança de requisições e processamento financeiro.
2. **Dashboard SaaS (Front-End):** Plataforma web voltada para clientes corporativos efetuarem a gestão de aplicações, licenças e métricas de uso.
3. **Painel Admin:** Ambiente restrito e invisível à rede pública, focado na auditoria global, logs de tráfego e acionamento de bloqueios emergenciais.
4. **Client SDKs:** Módulos enxutos integrados no software de terceiros, operando com latência otimizada para validação de licenças e biometria de hardware.

```mermaid
graph TD
    subgraph Client Environment
        SDK[Client SDKs / Softwares Terceiros]
    end

    subgraph Public Network
        FRONT[Dashboard SaaS<br/>authjtkeeste1991ka.squareweb.app]
    end

    subgraph Secure Internal Network
        API((API RESTful<br/>Endpoint Core))
        DB[(MongoDB Atlas<br/>Encrypted Storage)]
        ADMIN[Painel Admin<br/>Acesso Restrito]
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
