# BOTNET_INCIDENT_REPORT.md
Technical report on vulnerability detection and blocking (Botnet) scanning on a VPS server, using Wazuh in Docker. Blue Team case study. | Relatório técnico de detecção e bloqueio de varredura de vulnerabilidades (Botnet) em servidor VPS, utilizando Wazuh em Docker. Estudo de caso de Blue Team.

# 🛡️ Wazuh SIEM: Incident Analysis and Active Defense

**Project:** SIEM Implementation for VPS Monitoring
**Tool:** Wazuh (Docker Deployment)
**Incident Status:** 🟢 Blocked / Mitigated
**Date:** February/2026

## 📋 Project Summary
This repository documents the implementation of a defensive security infrastructure (Blue Team) using Wazuh. The objective was to protect a production server against automated scans and data exfiltration.

## 🚨 Incident Report: Botnet Detection

### The Scenario
During routine monitoring, the Wazuh agent detected a spike in anomalous requests coming from an external IP. The traffic was identified as a **brute-force scan**.

### Technical Analysis of the Attack
* **Attacker:** IP `45.135.193.11`
* **Attack Vector:** HTTP GET requests seeking sensitive configuration files:

* `/.env` (Application credentials)
* `/.aws/credentials` (AWS cloud keys)
* `/config.json`

### 🛡️ Defense (Mitigation)
The web server's security configuration, monitored by Wazuh, responded correctly to unauthorized access attempts.

* **Action:** Immediate blocking via HTTP response code.

* **Result:** 12 blocked attempts with **401 Unauthorized** status in <10 seconds.

## 📸 Evidence

### 1. Detection and Blocking Logs
*The log proves that the system identified the attempt to access critical files and denied access (Status 401).*
![Wazuh Logs]<img width="1366" height="768" alt="Real intrusion log to my VPS 05 02 2026" src="https://github.com/user-attachments/assets/8c99e1ed-1517-4b89-be5a-026b8124c6fd" />
<img width="1366" height="768" alt="Real intrusion log to my VPS 05 02 2026" src="https://github.com/user-attachments/assets/8c99e1ed-1517-4b89-be5a-026b8124c6fd" />

### 2. Operational Status (Dashboard)
*Overview of the system operating with integrity after the incident, demonstrating the stability of the Docker infrastructure.*
![Dashboard Wazuh]<img width="1364" height="688" alt="Dashboard Wazuh 5 2 2026" src="https://github.com/user-attachments/assets/5b5ec6c3-07b6-4d9d-a134-a4454903c87f" />
<img width="1364" height="688" alt="Dashboard Wazuh 5 2 2026" src="https://github.com/user-attachments/assets/5b5ec6c3-07b6-4d9d-a134-a4454903c87f" />

## 🚀 Conclusion
The implementation demonstrated the effectiveness of continuous monitoring. The visibility provided by Wazuh allowed us to validate that the firewall rules and web server configurations are effective against modern automated threats.

---
*Author: Rômulo*
*Tags: #Cybersecurity #BlueTeam #Wazuh #Docker #InfoSec*

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# 🛡️ Wazuh SIEM: Análise de Incidente e Defesa Ativa

**Projeto:** Implementação de SIEM para Monitoramento de VPS
**Ferramenta:** Wazuh (Docker Deployment)
**Status do Incidente:** 🟢 Bloqueado / Mitigado
**Data:** Fevereiro/2026

## 📋 Resumo do Projeto
Este repositório documenta a implementação de uma infraestrutura de segurança defensiva (Blue Team) utilizando o Wazuh. O objetivo foi proteger um servidor de produção contra varreduras automatizadas e exfiltração de dados.

## 🚨 Relatório de Incidente: Detecção de Botnet

### O Cenário
Durante o monitoramento de rotina, o agente do Wazuh detectou um pico de requisições anômalas vindo de um IP externo. O tráfego foi identificado como uma **varredura de força bruta (Brute-force/Scanning)**.

### Análise Técnica do Ataque
* **Atacante:** IP `45.135.193.11`
* **Vetor de Ataque:** Requisições HTTP GET buscando arquivos de configuração sensíveis:
    * `/.env` (Credenciais de aplicação)
    * `/.aws/credentials` (Chaves de nuvem AWS)
    * `/config.json`

### 🛡️ A Defesa (Mitigação)
A configuração de segurança do servidor web, monitorada pelo Wazuh, respondeu corretamente às tentativas de acesso não autorizado.
* **Ação:** Bloqueio imediato via código de resposta HTTP.
* **Resultado:** 12 tentativas bloqueadas com status **401 Unauthorized** em <10 segundos.

## 📸 Evidências

### 1. Logs de Detecção e Bloqueio
*O log comprova que o sistema identificou a tentativa de acesso a arquivos críticos e negou o acesso (Status 401).*
![Logs do Wazuh]<img width="1366" height="768" alt="log de invasão real à minha VPS 05 02 2026" src="https://github.com/user-attachments/assets/8c99e1ed-1517-4b89-be5a-026b8124c6fd" />
<img width="1366" height="768" alt="log de invasão real à minha VPS 05 02 2026" src="https://github.com/user-attachments/assets/8c99e1ed-1517-4b89-be5a-026b8124c6fd" />


### 2. Status Operacional (Dashboard)
*Visão geral do sistema operando com integridade após o incidente, demonstrando a estabilidade da infraestrutura Docker.*
![Dashboard Wazuh]<img width="1364" height="688" alt="Dashboard Wazuh 5 2 2026" src="https://github.com/user-attachments/assets/5b5ec6c3-07b6-4d9d-a134-a4454903c87f" />
<img width="1364" height="688" alt="Dashboard Wazuh 5 2 2026" src="https://github.com/user-attachments/assets/5b5ec6c3-07b6-4d9d-a134-a4454903c87f" />


## 🚀 Conclusão
A implementação demonstrou a eficácia do monitoramento contínuo. A visibilidade proporcionada pelo Wazuh permitiu validar que as regras de firewall e as configurações do servidor web estão efetivas contra ameaças automatizadas modernas.

---
*Autor: Rômulo*
