# 🛡️ Network Security Assessment & Server Hardening Lab

Este repositório documenta um laboratório prático focado em auditoria de rede, reconhecimento ativo com varredura furtiva, análise forense de pacotes e hardening de servidor Linux usando o Uncomplicated Firewall (UFW).

---

## 🚀 Arquitetura e Tecnologias do Laboratório

* **Sistema Operacional do Servidor (Analista/Hardening):** Ubuntu Server (Linux)
* **Sistema Operacional do Alvo/Gateway (Host):** Windows 11 (CPE: `cpe:/o:microsoft:windows`)
* **Interface de Rede (NIC):** `enp0s3` (QEMU virtual NIC / VirtualBox NAT) [MAC: `52:54:00:12:35:00`]
* **Endereçamento IP do Servidor:** `10.0.2.3/24`
* **Endereçamento IP do Gateway:** `10.0.2.1`
* **Ferramentas de Reconhecimento & Forense:** Nmap, Tcpdump & TShark
* **Ferramenta de Hardening:** UFW (Uncomplicated Firewall)

---

## 🔬 Etapas do Projeto

### 1. Diagnóstico de Conectividade e Roteamento
* Identificação da interface ativa (`enp0s3`) e verificação do endereçamento IP (`10.0.2.3/24`).
* Configuração e validação de rotas padrão via Netplan.
* Teste de conectividade e resolução de nomes até o gateway (`10.0.2.1`).

### 2. Reconhecimento Ativo (Stealth TCP SYN Scan)
Execução de varredura furtiva contra a superfície de ataque do gateway:
```bash
sudo nmap -sS -sV -p 21,22,23,80,135,139,445,3389 10.0.2.1
