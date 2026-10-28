# Phishing para Captura de Senhas em Ambiente Controlado

Este projeto consiste na simulação de um ataque de *Phishing* (Red Team) para captura de credenciais de acesso em um ambiente de laboratório controlado utilizando o VirtualBox.

**Aviso de Responsabilidade:** Este projeto foi realizado exclusivamente para fins educacionais e de estudo sobre segurança da informação em um ambiente estritamente isolado e controlado.

---

## Ambiente de Laboratório

O laboratório foi estruturado no VirtualBox utilizando 3 máquinas virtuais:

- **OPNsense:** Firewall responsável pelo roteamento e controle da rede.
- **Kali Linux:** Máquina atacante utilizada para hospedar a página de phishing e capturar as credenciais.
- **Windows 10:** Máquina vítima (com o firewall desabilitado para testes de tráfego sem bloqueios).

<!-- Adicione sua imagem do VirtualBox aqui: ![Maquinas Virtuais](./caminho-da-imagem.png) -->

---

## Configurações de Rede

- **Rede LAN:** `10.20.120.0/24`
- **IP do Kali Linux (Atacante):** `10.20.120.102`
- **IP do Windows 10 (Vítima):** `10.20.120.103`

---

## Ferramentas Utilizadas

- **Kali Linux**
- **SET (Social-Engineer Toolkit / `setoolkit`)**
- **VirtualBox**
- **OPNsense Firewall**

---

## Passo a Passo da Execução

### 1. Configuração do Phishing no Kali Linux

No terminal do Kali Linux, executou-se os seguintes passos dentro do **SET (Social-Engineer Toolkit)**:

1. Obter acesso de superusuário:
   ```bash
   sudo su
   ```
2. Iniciar a ferramenta:
   ```bash
   setoolkit
   ```
3. Selecionar o tipo de ataque:
   - `1) Social-Engineering Attacks`
   - `2) Web Site Attack Vectors`
   - `3) Credential Harvester Attack Method`
   - `3) Custom Import`

*Nota: Devido a mecanismos de proteção ao tentar clonar diretamente páginas de login de serviços como Facebook ou Instagram, foi desenvolvido um arquivo `index.html` personalizado simulando uma tela de login para garantir a execução do teste.*

---

### 2. Simulação e Captura

1. A página falsa foi disponibilizada no endereço IP do Kali Linux (`10.20.120.102`).
2. A partir da máquina Windows 10, o usuário acessou o IP e inseriu credenciais de teste na interface de login.

<!-- Adicione a Imagem 1 aqui: ![Tela de Login](./caminho-imagem-login.png) -->

3. Após a submissão dos dados na página web, o `setoolkit` interceptou a requisição e exibiu em tempo real as credenciais capturadas no terminal do Kali Linux (`email` e `password`).

<!-- Adicione a Imagem 2 aqui: ![Captura de Credenciais](./caminho-imagem-terminal.png) -->

---

## Resultados

O teste de conceito demonstrou com sucesso a eficácia da engenharia social via captura de credenciais quando não há controles de segurança ativos no endpoint ou navegação na rede.

Imagem do index.html

<img width="567" height="410" alt="image" src="https://github.com/user-attachments/assets/fed53949-e7bb-481a-93ac-cbbc25128344" />

Captura Após inserção das credenciais

<img width="567" height="200" alt="image" src="https://github.com/user-attachments/assets/327584f5-c979-42ad-9d3a-17fab1e31b23" />
