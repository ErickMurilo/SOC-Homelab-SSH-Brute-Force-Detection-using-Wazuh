# Soc Homlab-SSH-Brute-force

Este projeto demonstra uma simulação e detecção de ponta a ponta de um ataque de força bruta SSH, utilizando um ambiente de laboratório doméstico (homelab) de SOC com Kali Linux, um agente Ubuntu e o Wazuh SIEM.

O objetivo principal foi simular um ataque de força bruta SSH utilizando o Hydra, gerar logs de falha de autenticação e investigar alertas por meio do recurso de *Threat Hunting* do Wazuh.

- Simulação de brute force SSH com Hydra
- Coleta de logs em ambiente Linux
- Monitoramento em tempo real no Wazuh
- Investigação de IOC (Indicators of Compromise)

# Ferramentas Utilizadas

- Wazuh SIEM
- Kali Linux
- Hydra
- SSH

# Objetivo

O objetivo central deste lab foi simular um ataque real de brute force contra SSH e analisar o processo completo de detecção em um ambiente SOC.



# Incident Analysis

A análise completa do incidente contendo investigação dos logs, eventos correlacionados e alertas gerados pelo Wazuh está disponível no link abaixo:

[Acesse o relatório completo do incidente.](https://github.com/ErickMurilo/SOC-Homelab-SSH-Brute-Force-Detection-using-Wazuh/blob/main/SSH-Brute-Force-Detection-with-Wazuh.md)
