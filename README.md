<div align="center">

# SecAuth (Projeto Sentinela)
**Enterprise Security-as-a-Service Infrastructure**

[![Status: Production MVP](https://img.shields.io/badge/Status-Production_MVP-success?style=flat-square)](#)
[![Security: AES-256-GCM](https://img.shields.io/badge/Encryption-AES--256--GCM-blue?style=flat-square)](#)
[![Security: HMAC-SHA256](https://img.shields.io/badge/Signatures-HMAC--SHA256-blue?style=flat-square)](#)

🔗 **Acesso ao Ambiente MVP:** [authjtkeeste1991ka.squareweb.app](https://authjtkeeste1991ka.squareweb.app)

</div>

---

## 👨‍💻 Arquitetura e Engenharia (Desenvolvimento Solo)

**A arquitetura de proteção de todo o sistema foi desenhada 100% por mim**, estruturada rigorosamente para atender às exigências de segurança de alto nível do cliente. Atuei de forma solo em todas as frentes do projeto:

* **Full-Stack & UX:** Criação do SaaS, Painel do Cliente, Painel Admin e SDKs.
* **Cyber Security:** Blindagem contra engenharia reversa, *Replay Attacks*, *Man-in-the-Middle* e testes de intrusão.
* **DevOps:** Deploy isolado, orquestração de rotas e banco de dados particionado.

---

## 💻 Stack Tecnológica

<p align="left">
  <img src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Express.js-404D59?style=for-the-badge" alt="Express.js" />
  <img src="https://img.shields.io/badge/MongoDB_Atlas-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB Atlas" />
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS" />
  <img src="https://img.shields.io/badge/Vite-B73BFE?style=for-the-badge&logo=vite&logoColor=FFD62E" alt="Vite" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
</p>

---

## 🔒 Mecanismos de Proteção e Isolamento

Em vez de longos textos, eis a infraestrutura tática implementada:

* **AES-256-GCM:** *Payloads* HTTP 100% encriptados de ponta-a-ponta.
* **HMAC-SHA256:** Assinaturas digitais nos pacotes do SDK (Zero chaves expostas na rede).
* **HWID Lock:** Licenças vinculadas ao hardware físico (MAC, CPU) do usuário final.
* **Anti-Replay Attack:** Bloqueio temporal com uso de *Nonces* únicos (tolerância em milissegundos).
* **Isolamento de Redes:** Back-End, Front-End (Cliente) e Admin particionados fisicamente.

```mermaid
graph TD
    SDK[SDKs / Client Apps] == "Assinatura HMAC + HWID" ==> API((Core API RESTful))
    FRONT[Dashboard do Cliente] <== "AES-256-GCM (Payload Sec)" ==> API
    API <== "Private Peering" ==> DB[(MongoDB Atlas)]
    ADMIN[Painel Admin Restrito] <== "Auditoria Segura" ==> API
    
    classDef secure fill:#0f172a,stroke:#38bdf8,stroke-width:2px,color:#f8fafc;
    class API secure;
