# SecAuth - Enterprise Security-as-a-Service Infrastructure

**SecAuth** é uma infraestrutura B2B de *Security-as-a-Service* (SECaaS) projetada para fornecer licenciamento, autenticação e proteção criptográfica a softwares suscetíveis a engenharia reversa, pirataria e interceptação de dados.

**Ambiente MVP (Produção):** [https://authjtkeeste1991ka.squareweb.app](https://authjtkeeste1991ka.squareweb.app)

---

## Topologia de Arquitetura e Isolamento de Rede

O ecossistema foi projetado sob o paradigma de **Privilégio Mínimo e Particionamento Estrito**. A arquitetura divide-se em nós independentes, operando em domínios isolados para mitigar riscos de comprometimento lateral.

Abaixo, o diagrama de topologia ilustra o fluxo de dados e o endereçamento de cada componente:

```mermaid
graph TD
    subgraph Client Environment
        SDK[Client SDK / Desktop Apps<br/>End-User Execution]
    end

    subgraph Public Network
        FRONT[SaaS Dashboard<br/>URL: authjtkeeste1991ka.squareweb.app]
    end

    subgraph Secure VPC / Internal Network
        API((Core API<br/>URL: Endpoint Isolado))
        DB[(MongoDB Atlas<br/>Encrypted Storage)]
        ADMIN[Admin Panel<br/>URL: Restrita / Acesso VPN]
    end

    %% Connections
    SDK -->|HMAC-SHA256 Signatures<br/>HWID Verification| API
    FRONT <-->|AES-256-GCM Payload<br/>End-to-End Encrypted| API
    API <-->|Private Peering| DB
    ADMIN <-->|Encrypted Audit & Control| API

    classDef public fill:#f4f6f8,stroke:#cbd5e1,stroke-width:2px,color:#334155;
    classDef secure fill:#e2e8f0,stroke:#94a3b8,stroke-width:2px,color:#0f172a;
    classDef core fill:#1e293b,stroke:#0f172a,stroke-width:2px,color:#f8fafc;
    
    class FRONT,SDK public;
    class ADMIN,DB secure;
    class API core;
