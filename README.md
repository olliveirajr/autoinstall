# 🚀 Ubuntu Desktop 24.04

![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-E95420?logo=ubuntu\&logoColor=white)
![Cloud-Init](https://img.shields.io/badge/Cloud--Init-Autoinstall-blue)
![Docker](https://img.shields.io/badge/Docker-Installed-2496ED?logo=docker\&logoColor=white)
![LVM](https://img.shields.io/badge/Storage-LVM-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

Provisionamento automatizado do **Ubuntu Desktop 24.04** utilizando **Cloud-Init Autoinstall**.

## 📋 Sobre o Projeto

Este repositório contém um arquivo `autoinstall.yaml` que realiza a instalação automatizada do Ubuntu Desktop com:

* 🔐 Particionamento automático via LVM
* 👤 Criação de usuário padrão
* 🌎 Configuração regional (pt_BR / America-Cuiaba)
* 🐳 Instalação oficial do Docker
* 🖥 Oh My Bash com tema `lambda`
* ⚡ Autocomplete para git, docker e ssh
* 🔥 Firewall configurado via UFW

Projeto ideal para:

* Workstations
* Homelabs
* Máquinas de laboratório
* Ambientes de teste reproduzíveis

## 🧱 Arquitetura do Provisionamento

```text
Ubuntu Desktop 24.04
│
├── LVM automático
├── Usuário padrão (sudo)
├── Pacotes base
├── Docker CE + Compose v2
├── Oh My Bash (lambda)
├── Bash-completion
└── UFW habilitado
```

## ⚙️ Componentes Instalados

### 🖥 Sistema Base

* Hostname: `workstation`
* Locale: `pt_BR.UTF-8`
* Timezone: `America/Cuiaba`
* SSH Server habilitado

### 📦 Pacotes adicionais

* curl
* wget
* git
* htop
* net-tools
* jq
* tree
* bash-completion
* ufw

### 🐳 Docker

Instalado via repositório oficial da Docker:

* docker-ce
* docker-ce-cli
* containerd
* docker-buildx-plugin
* docker-compose-plugin

Usuário incluído automaticamente no grupo `docker`.

---

## 💻 Terminal Customizado ( Oh My Bash )

* Instalação automática
* Tema: `lambda`
* Plugins desativados para evitar conflitos

## 🔐 Firewall

```text
Default: deny incoming
Default: allow outgoing
OpenSSH liberado
UFW habilitado
```

## 🚀 Como Utilizar

### Durante a instalação do Ubuntu Desktop

Selecione:

> Instalação automatizada

Cole a URL do arquivo RAW.

```
https://raw.githubusercontent.com/olliveirajr/autoinstall/refs/heads/main/autoinstall.yaml
```

## 🔑 Gerar senha criptografada

A senha deve estar no formato SHA-512:

```bash
openssl passwd -6 "PASSWORD"
```

Substitua o valor no campo:

```yaml
password: "$6$..."
```

## 📌 Segurança

⚠️ Recomendações para produção:

* Utilizar autenticação SSH por chave pública
* Desabilitar login por senha (`allow-pw: false`)
* Ajustar regras adicionais de firewall conforme necessidade

## 🔄 Personalização

Possíveis extensões:

* Instalar kubectl
* Instalar Helm
* Configurar NFS automático
* Criar partição separada para `/var/lib/docker`

## 📖 Referência Oficial

- [Autoinstall configuration reference manual](https://canonical-subiquity.readthedocs-hosted.com/en/latest/reference/autoinstall-reference.html)
