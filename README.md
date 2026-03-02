# 🛡️ SecAuth (Projeto Sentinela)

**SecAuth** é uma startup de *Security-as-a-Service* que oferece um ecossistema completo de criptografia, licenciamento e autenticação para softwares com alto risco de serem crackeados, pirateados ou sofrerem engenharia reversa.

> 🚀 **Acesso ao MVP:** [https://authjtkeeste1991ka.squareweb.app](https://authjtkeeste1991ka.squareweb.app)

---

## 👤 Sobre a Engenharia (O Fundador)

Este projeto foi idealizado, arquitetado e **desenvolvido 100% de forma solo**. Todo o ciclo de vida da aplicação foi executado por mim, abrangendo:
* **Engenharia de Software (Full-Stack):** Criação das interfaces, lógicas de backend, SDKs e integrações de pagamento.
* **DevOps:** Configuração de servidores, deploy isolado, banco de dados (MongoDB Atlas) e roteamento de redes.
* **Pentest & Cyber Security:** Testes de invasão, auditoria de código, blindagem contra *Replay Attacks*, injeções, *Brute-force* e quebra de pacotes.

---

## 🏗️ Arquitetura de Particionamento Isolado

Para garantir a máxima integridade, o sistema utiliza um **método de particionamento estrito**. Os módulos não se misturam, operando em ambientes isolados que comunicam apenas através da nossa API blindada:

1. **Back-End (O Cofre):** Uma API RESTful isolada, responsável por toda a validação de segurança, comunicação com a base de dados, gestão do Checkout e emissão de chaves.
2. **Front-End (Painel do Cliente):** A Landing Page e o Dashboard (SaaS) onde os programadores e empresas gerem os seus softwares, licenças e clientes.
3. **Painel Admin (A Torre de Controlo):** Um ambiente completamente separado, acessível apenas à administração da SecAuth, para monitorização de tráfego, gestão de planos de assinatura e *kill-switches*.
4. **SDKs / Client Apps:** Módulos de integração leves que os clientes embutem nos seus softwares (C++, Python, NodeJS) para se ligarem à API.

---

## 🔒 Escopo de Proteção Militar

O sistema não se baseia em simples tokens JWT para o software final, mas sim em primitivas criptográficas robustas:

* **Muralha AES-256-GCM:** Toda a comunicação entre o Painel Web e o Backend trafega com o "corpo" (payload) inteiramente encriptado ponta-a-ponta, prevenindo interceções (*Man-in-the-Middle*).
* **Assinaturas HMAC-SHA256:** As requisições dos softwares desktop (SDK) não enviam chaves puras. Elas geram uma assinatura usando a Chave Secreta (`Secret Key`), garantindo a autenticidade do pacote.
* **Anti-Replay Attack & Timestamping:** Uso de `Nonces` únicos e `Timestamps` com tolerância de 2 minutos. Mesmo que um atacante intercete a rede, não pode repetir o envio do pacote.
* **HWID Lock (Hardware ID):** A licença liga-se permanentemente à impressão digital do Hardware (MAC Address, CPU, Placa-mãe) do utilizador final.
* **Anti-Flood & Rate Limiting:** Middlewares de proteção contra *DDoS* e ataques de *Brute-force* nas tentativas de login/validação.

---

## 💻 Tecnologias Utilizadas

O ecossistema foi construído sobre uma stack moderna, escalável e tipada:

<p align="left">
  <img src="https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Express.js-404D59?style=for-the-badge" />
  <img src="https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white" />
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" />
  <img src="https://img.shields.io/badge/Vite-B73BFE?style=for-the-badge&logo=vite&logoColor=FFD62E" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
</p>

---

## 📸 Galeria do Sistema

### Landing Page (Apresentação do SaaS)
<a href="https://postimg.cc/YGvD1HC5" target="_blank">
  <img src="https://i.postimg.cc/fLC4QWnR/imagem-2026-03-01-161904068.png" alt="Landing Page 1" width="800">
</a>

<a href="https://postimg.cc/nXK9FRqZ" target="_blank">
  <img src="https://i.postimg.cc/52TBmD0H/imagem-2026-03-01-174712923.png" alt="Landing Page 2" width="800">
</a>

### Dashboard do Cliente (Visão Geral)
<a href="https://postimg.cc/tnPCrJ5Z" target="_blank">
  <img src="https://i.postimg.cc/5yKY2FQ3/imagem-2026-03-01-174938118.png" alt="Dashboard" width="800">
</a>

### Configurações da Aplicação (AppID e Secret)
<a href="https://postimg.cc/2LFNbZGL" target="_blank">
  <img src="https://i.postimg.cc/4yjf0vhP/imagem-2026-03-01-175216950.png" alt="Configurações do Perfil" width="800">
</a>

### Gestão de Assinaturas (Checkout & Planos)
<a href="https://postimg.cc/Vrn3pC3F" target="_blank">
  <img src="https://i.postimg.cc/QtyhBgmv/imagem-2026-03-01-175307736.png" alt="Assinaturas" width="800">
</a>

### Gestão Interna da App (Licenças e Utilizadores)
<a href="https://postimg.cc/NKVGwRzt" target="_blank">
  <img src="https://i.postimg.cc/q7BNyLcN/imagem-2026-03-01-175403656.png" alt="Interface Interna do App" width="800">
</a>

### Visão das Chaves (API Integrada)
<a href="https://postimg.cc/sGVsJmv7" target="_blank">
  <img src="https://i.postimg.cc/vTnTbSyq/imagem-2026-03-01-175444791.png" alt="API no App" width="800">
</a>

---

> **Desenvolvido com 🔒 Segurança e ⚡ Performance para revolucionar o mercado de autenticação de software.**
