# cybersecurity-bruteforce-medusa
# Auditoria de Segurança: Ataques de Força Bruta e Medidas de Prevenção

Este projeto faz parte da formação em Cibersegurança da DIO e demonstra a implementação de ataques de força bruta em ambiente controlado, utilizando o **Kali Linux** e a ferramenta **Medusa**, com foco em análise de vulnerabilidades e estratégias de mitigação.

## Cenário do Laboratório
O ambiente foi estruturado em uma rede isolada (Host-Only) para garantir a segurança dos testes:
- **Atacante:** Kali Linux
- **Alvo:** Metasploitable 2 (Ambiente vulnerável)
- **Ferramentas:** Nmap (Reconhecimento) e Medusa (Exploração de credenciais)

## Execução Técnica

### 1. Mapeamento de Superfície (Nmap)
Identificação de serviços abertos no alvo:
- **Porta 21 (FTP):** Serviço de transferência de arquivos em texto claro.
- **Portas 139/445 (SMB):** Protocolo de compartilhamento de recursos em rede.
- **Porta 80 (HTTP):** Interface web rodando a aplicação DVWA.

### 2. Simulação de Ataque com Medusa
Foram realizados ataques baseados em dicionário para validar a robustez das credenciais:
- **FTP:** `medusa -h [IP_ALVO] -u msfadmin -P wordlist.txt -M ftp`
- **SMB:** `medusa -h [IP_ALVO] -u admin -P wordlist.txt -M smbnt`

## Estratégias de Mitigação (Prevenção)
Para proteger uma infraestrutura real contra esses ataques, as seguintes medidas são recomendadas:

1. **Implementação de Fail2Ban:** Bloqueio automático de IPs após sucessivas tentativas falhas de login.
2. **Uso de Protocolos Seguros:** Substituição do FTP por SFTP (SSH File Transfer Protocol) para criptografia de dados e credenciais.
3. **MFA (Autenticação de Múltiplos Fatores):** Exigência de um segundo fator de validação para acessos administrativos.
4. **Políticas de Senhas Fortes:** Implementação de requisitos de complexidade para inviabilizar ataques por dicionários comuns.
5. **Monitoramento de Logs:** Auditoria ativa de acessos para detecção precoce de tentativas de intrusão.

---
*Projeto desenvolvido como parte do aprendizado em segurança de redes e defesa cibernética.*
