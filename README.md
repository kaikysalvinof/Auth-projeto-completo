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
```

---

## Escopo de Proteção e Primitivas Criptográficas

A plataforma afasta-se de mecanismos de validação vulneráveis em aplicações nativas, adotando um padrão de defesa de nível militar focado na integridade do pacote:

* **Muralha AES-256-GCM:** O tráfego bidirecional entre o Painel Web e a API trafega com o payload inteiramente ofuscado de ponta a ponta.
* **Assinaturas HMAC-SHA256:** Aplicações clientes (SDKs) não transmitem chaves de API expostas na rede. A autenticidade é atestada assinando matematicamente o pacote, preservando a Secret Key.
* **Hardware ID Lock (HWID):** O sistema realiza a leitura física do hardware (MAC Address, CPU). A licença é permanentemente fixada à máquina do usuário final, anulando o compartilhamento ilícito.
* **Anti-Replay Attack e Timestamping:** Incorporação de Nonces criptográficos únicos aliados à tolerância de tempo restrita (milissegundos) para invalidar pacotes interceptados e clonados.
* **Anti-Flood e Rate Limiting:** Middlewares de bloqueio na borda da aplicação para neutralizar ataques DDoS direcionados e automatizações maliciosas.

---

## Stack Tecnológica

A infraestrutura foi consolidada com tecnologias corporativas para suportar concorrência I/O e assegurar tipagem estrita de dados:

**Front-End (Web SaaS & Admin):**
<br>
<img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
<img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
<img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
<img src="https://img.shields.io/badge/Vite-B73BFE?style=for-the-badge&logo=vite&logoColor=FFD62E" alt="Vite" />

**Back-End (Core API & SDKs):**
<br>
<img src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js" />
<img src="https://img.shields.io/badge/Express.js-404D59?style=for-the-badge" alt="Express.js" />
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />

**Database (Persistência e Segurança):**
<br>
<img src="https://img.shields.io/badge/MongoDB_Atlas-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB Atlas" />

---

## Interface de Operações e Módulos do Sistema

Abaixo encontra-se a galeria detalhada das interfaces desenvolvidas, cobrindo o painel comercial, gestão interna de licenciamento e módulos financeiros.

<table align="center" style="border: none; text-align: center;">
<tr>
<td width="50%">
<b>Apresentação B2B (Landing Page Hero)</b><br><br>
<a href="https://postimg.cc/YGvD1HC5" target="_blank"><img src="https://i.postimg.cc/fLC4QWnR/imagem-2026-03-01-161904068.png" alt="Apresentação Comercial SecAuth" width="100%"></a>
</td>
<td width="50%">
<b>Apresentação B2B (Recursos e Defesa)</b><br><br>
<a href="https://postimg.cc/nXK9FRqZ" target="_blank"><img src="https://i.postimg.cc/52TBmD0H/imagem-2026-03-01-174712923.png" alt="Recursos e Proteção" width="100%"></a>
</td>
</tr>
<tr>
<td width="50%">
<b>Dashboard Geral do Cliente (SaaS)</b><br><br>
<a href="https://postimg.cc/tnPCrJ5Z" target="_blank"><img src="https://i.postimg.cc/5yKY2FQ3/imagem-2026-03-01-174938118.png" alt="Painel de Controle do Cliente" width="100%"></a>
</td>
<td width="50%">
<b>Configurações da Aplicação (AppID e Secret)</b><br><br>
<a href="https://postimg.cc/2LFNbZGL" target="_blank"><img src="https://i.postimg.cc/4yjf0vhP/imagem-2026-03-01-175216950.png" alt="Configurações de Credenciais" width="100%"></a>
</td>
</tr>
<tr>
<td width="50%">
<b>Gestão Interna (Controle de Licenças e Usuários)</b><br><br>
<a href="https://postimg.cc/NKVGwRzt" target="_blank"><img src="https://i.postimg.cc/q7BNyLcN/imagem-2026-03-01-175403656.png" alt="Gestão Interna de Licenças" width="100%"></a>
</td>
<td width="50%">
<b>Integração Direta e Monitoramento (API)</b><br><br>
<a href="https://postimg.cc/sGVsJmv7" target="_blank"><img src="https://i.postimg.cc/vTnTbSyq/imagem-2026-03-01-175444791.png" alt="Monitoramento e API" width="100%"></a>
</td>
</tr>
<tr>
<td width="100%" colspan="2">
<b>Módulo Financeiro e Checkout de Assinaturas</b><br><br>
<a href="https://postimg.cc/Vrn3pC3F" target="_blank"><img src="https://i.postimg.cc/QtyhBgmv/imagem-2026-03-01-175307736.png" alt="Planos e Assinaturas" width="50%"></a>
</td>
</tr>
</table>
