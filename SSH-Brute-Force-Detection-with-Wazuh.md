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

Para permitir a comunicação entre as máquinas virtuais do laboratório, foi criada uma NAT Network no Oracle VirtualBox chamada NatNetwork, utilizando a faixa de IP 10.0.2.0/24.
Essa configuração possibilita que todos os dispositivos do ambiente compartilhem a mesma rede virtual, garantindo conectividade entre atacante, servidor Wazuh e máquina monitorada. 

<img width="300" height="180" alt="adaptador de rede" src="https://github.com/user-attachments/assets/471ad8ec-3134-4774-b86d-82fce39484cc" />

Cada VM foi configurada no Adaptador 1 usando o modo Rede NAT, associada à rede virtual NatNetwork, garantindo conectividade necessária para simulação do ataque de força bruta via SSH.

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

Para simular um ataque de força bruta via SSH, foram criados dois arquivos no Kali Linux:

usuarios.txt -> contendo os usuários a serem testados
senhas.txt ->contendo a wordlist de senhas

Em seguida, foi utilizada a ferramenta Hydra para automatizar tentativas de autenticação contra o serviço SSH da máquina alvo (10.0.2.5).

## Detecção no Wazuh 

<img width="600" height="300" alt="autentication failure" src="https://github.com/user-attachments/assets/24297292-ec3f-4601-9329-cd9b39d81b3a" />

Após a execução do ataque de brute force via Hydra, o dashboard do Wazuh registrou um volume anormal de tentativas de autenticação SSH, permitindo identificar atividade suspeita em tempo real.

<img width="600" height="300" alt="print 434343" src="https://github.com/user-attachments/assets/5db673c3-0bc6-4127-82a4-c7f584bd68df" />

Após a detecção inicial no dashboard, foi realizada uma análise detalhada dos eventos na aba Threat Hunting do Wazuh, permitindo inspecionar os logs gerados durante o ataque brute force via SSH.
Os logs mostram diversas tentativas consecutivas de autenticação em um curto intervalo de tempo, indicando comportamento compatível com brute force.


<img width="300" height="300" alt="detalhes ataque" src="https://github.com/user-attachments/assets/96ba95dd-37fe-4fc6-b0d7-c9876511c625" />

Para aprofundar a investigação, foi analisado o documento detalhado do alerta no Wazuh, permitindo visualizar os campos extraídos do log SSH e identificar origem, destino e contexto da tentativa de autenticação maliciosa.


## Indicadores de Comprometimento (IOCs)

- Endereço IP de Origem: 10.0.2.6
- Endereço IP de Destino: 10.0.2.5
- Conta Alvo: erick
- Categoria do Ataque: Brute Force via SSH
- Ferramenta de Ataque: Hydra

## Mitigações

- MFA (Autenticação Multifator)
- Fail2Ban para bloqueio automático
- Strong Password Policies

## Conclusão

Este laboratório demonstrou como ataques automatizados de SSH Brute Force podem ser identificados em um ambiente SOC utilizando Wazuh SIEM.
A simulação permitiu observar o ciclo completo de um incidente de segurança: execução do ataque, geração de eventos, detecção em tempo real e análise dos alertas.
Foi possível identificar padrões característicos de brute force através da correlação de logs de autenticação, frequência de tentativas e origem do tráfego.
