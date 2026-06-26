## Setup Machines


- Wazuh Server 

Ubuntu 24.04

4 CPU

8GB RAM

80GB Disk

- Agent Ubuntu

Wazuh Agent

SSH Server

- Attacker

Kali Linux

Hydra

## Ambiente do Lab

<img width="550" height="140" alt="natnetwork" src="https://github.com/user-attachments/assets/2ab1e5ab-ca2e-40f6-b2e1-e07bbf537812" />

Criamos um natnetwork, 

<img width="300" height="180" alt="adaptador de rede" src="https://github.com/user-attachments/assets/471ad8ec-3134-4774-b86d-82fce39484cc" />

colocamos os 3 dispositivos na natnetwork, rede nat para se enxergarem

### ip da Máquina Kali Linux
<img width="600" height="100" alt="ip kali" src="https://github.com/user-attachments/assets/1e796755-5757-4b77-bb38-3938a02eddbf" />

### ip da Máquina com Agente
<img width="600" height="100" alt="ip agente" src="https://github.com/user-attachments/assets/a335caa7-99ed-48a6-9ca9-79fac2b85093" />

### ip da Máquina Server Wazuh
<img width="600" height="100" alt="ip server" src="https://github.com/user-attachments/assets/fd6e28d6-506b-4d1c-98e3-b571b12b438d" />

## Instalação Dos Programas 

- Wazuh Server

curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh

sudo bash wazuh-install.sh -a

- Agent

sudo apt install wazuh-agent

sudo apt install openssh-server

- Kali

sudo apt install hydra

## Simulação do Ataque

<img width="550" height="150" alt="hydra rodando" src="https://github.com/user-attachments/assets/4cc498fc-7c7d-4182-be90-45c9f1aa0ce0" />

## Detecção no Wazuh 

<img width="600" height="300" alt="autentication failure" src="https://github.com/user-attachments/assets/24297292-ec3f-4601-9329-cd9b39d81b3a" />
<img width="600" height="300" alt="print 434343" src="https://github.com/user-attachments/assets/5db673c3-0bc6-4127-82a4-c7f584bd68df" />



<img width="300" height="300" alt="detalhes ataque" src="https://github.com/user-attachments/assets/96ba95dd-37fe-4fc6-b0d7-c9876511c625" />

## Indicadores de Comprometimento (IOCs)


Source IP: 10.0.2.6

Destination IP: 10.0.2.5

Target User: erick

Attack Type: SSH Brute Force

Tool Used: Hydra


## MITRE ATT&CK Mapping

T1110 — Brute Force

T1110.001 — Password Guessing

## Mitigações 

MFA

Fail2Ban

SSH Hardening

Rate Limiting

Strong Password Policies

## Conclusão

attack simulation

detection

threat hunting

SOC workflow
