# ROADMAP TI → ESPAÑA v2.0 — MASTER PLAN

## Missão

Em 6 meses, sair de **“sei os conceitos”** para:

> **“Sei me virar.”**

Isso significa conseguir **construir, operar, quebrar, diagnosticar, recuperar, automatizar e explicar** uma pequena infraestrutura moderna.

O roadmap original continua sendo a base. Esta versão reorganiza a prioridade, transforma conteúdo em prática e faz do **ISP Infrastructure Lab** o projeto-fio-condutor.

---

## Regra de prioridade

### CORE — obrigatório
Redes, Linux, Git/GitHub, Docker/Compose, HTTP/API, AWS (IAM/VPC/EC2/S3/CloudWatch), Terraform, GitHub Actions, troubleshooting, observabilidade, segurança básica e inglês técnico.

### IMPORTANT — saber explicar e aplicar quando necessário
LVM, VLAN, IPv6, EFS, NACL, backup/DR, estratégias de deploy, módulos Terraform, PromQL, secrets managers.

### BÔNUS — não pode atrasar o projeto
Azure prático, Kubernetes, Vault profundo, Ansible, Jenkins, rebase avançado, tracing avançado.

**Regra:** nunca sacrificar CORE para “terminar mais tecnologias”.

---

# Projeto-fio-condutor: ISP Infrastructure Lab

O laboratório evolui durante os 6 meses.

### Fase 1 — servidor
Linux + SSH + firewall + serviços + logs + troubleshooting.

### Fase 2 — aplicação
Git + Docker + Compose + API + banco + proxy.

### Fase 3 — cloud
VPC + subnets + routes + Security Groups + EC2 + S3 + CloudWatch.

### Fase 4 — IaC
Recriar a infraestrutura inteira com Terraform.

### Fase 5 — CI/CD
Commit → testes → build Docker → registry → deploy → rollback.

### Fase 6 — operação
Métricas + logs + alertas + segurança + incidentes + documentação + apresentação em inglês.

---

# MÊS 01 — FUNDAMENTOS / OPS CORE

## Semana 01 — TCP/IP + Linux CLI
**Estudar**
- OSI vs TCP/IP
- IPv4, CIDR e subnetting
- TCP/UDP
- portas
- `ip addr`, `ip route`, `ss`
- `ping`, `traceroute`/`tracepath`, `mtr`

**Lab**
- dividir uma /24 em sub-redes
- mapear interfaces/rotas
- diagnosticar uma porta inacessível

**Gate**
> Explico o caminho de um pacote e consigo separar problema de IP, rota e porta.

## Semana 02 — DNS + HTTP/HTTPS
**Estudar**
- resolução recursiva/autoritativa
- A, AAAA, CNAME, MX, TXT, NS, SOA
- TTL/cache
- HTTP methods/status/headers
- TLS
- cookies, sessão, CORS

**Lab**
- `dig` completo
- `curl -I` e `curl -v`
- incidentes 404/403/502

**Gate**
> Consigo investigar “site não abre” camada por camada.

## Semana 03 — Linux administration
**Estudar**
- FHS
- permissões
- usuários/grupos
- sudo
- processos/sinais
- apt
- systemd
- journalctl

**Lab**
- criar serviço `.service`
- criar usuário não-root
- diagnosticar serviço que falha

## Semana 04 — SSH + hardening + incidentes
**Estudar**
- SSH keys/config
- UFW/iptables conceito
- disco: `df`, `du`, `lsblk`, `mount`
- cron
- grep/sed/awk
- fail2ban conceito

**Lab**
- SSH por chave
- firewall mínimo
- 3 incidentes artificiais
- post-mortem

### GATE 01
> Entro, protejo, observo e recupero um Linux remoto.

---

# MÊS 02 — GIT + DOCKER / BUILD

## Semana 05 — Git
- init/clone/add/commit/status/log/diff
- branches
- merge
- conflitos
- `.gitignore`
- commits explicáveis

**Lab:** primeiro repositório do ISP Infrastructure Lab.

## Semana 06 — GitHub
- README
- PR
- Issues
- releases/tags
- documentação em inglês

**Lab:** README operacional completo.

## Semana 07 — Docker
- imagem vs container vs registry
- layers/cache
- Dockerfile
- volumes
- redes
- logs/exec
- multi-stage build

**Lab:** containerizar aplicação.

## Semana 08 — Compose + APIs
- Compose
- múltiplos serviços
- `.env`
- health checks
- curl
- JSON
- API key/Bearer/Basic
- webhooks

**Lab:** app + banco + proxy.

### GATE 02
> Subo uma stack multi-container e explico a rede entre os serviços.

---

# MÊS 03 — AWS / CLOUD

## Semana 09 — Cloud + IAM
- IaaS/PaaS/SaaS
- regiões/AZ
- responsabilidade compartilhada
- IAM users/groups/roles/policies
- least privilege

**Lab:** identidade de laboratório com privilégio mínimo.

## Semana 10 — VPC
- CIDR
- subnets públicas/privadas
- route tables
- Internet Gateway
- NAT Gateway
- Security Groups vs NACLs

**Lab:** desenhar a VPC antes de criá-la.

## Semana 11 — EC2 + S3
- AMI
- key pair
- user data
- IP público/privado
- S3
- EBS vs EFS
- custos

**Lab:** EC2 com bootstrap + S3.

## Semana 12 — Cloud operations
- CloudWatch
- métricas/logs/alarmes
- billing alerts
- backups
- RPO/RTO

**Lab:** simular falha e produzir post-mortem.

### GATE 03
> Opero uma pequena arquitetura AWS e consigo explicar o caminho do tráfego e as permissões.

---

# MÊS 04 — TERRAFORM / IaC

## Semana 13 — Terraform core
- IaC
- provider
- resources
- data sources
- init/plan/apply/destroy
- state

## Semana 14 — Configuração
- variables
- locals
- outputs
- tfvars
- expressions

## Semana 15 — Organização
- módulos
- state remoto
- locking
- estrutura de projeto

## Semana 16 — Lab IaC completo
Recriar:
- VPC
- subnets
- routes
- SG
- EC2
- S3

### GATE 04
> Recrio o ambiente de forma reproduzível e sei ler um `terraform plan`.

---

# MÊS 05 — CI/CD + OBSERVABILIDADE

## Semana 17 — GitHub Actions
- workflows
- triggers
- jobs
- steps
- runners
- secrets
- artifacts

## Semana 18 — Build/deploy
- Docker build
- tags
- registry
- deploy
- rollback

**Pipeline-alvo**

`git push → test → build → image → registry → deploy`

## Semana 19 — Observabilidade
- logs vs métricas vs traces
- Prometheus
- scrape
- PromQL básico
- Grafana
- dashboards
- alertas

## Semana 20 — Failure engineering
Quebrar propositalmente:
- DNS
- porta
- firewall
- container
- dependência
- processo
- configuração

### GATE 05
> Detecto, investigo e recupero uma falha usando evidências.

---

# MÊS 06 — PRODUÇÃO / PORTFÓLIO / ESPANHA

## Semana 21 — Segurança
- least privilege
- secrets
- dependency scanning
- SSH hardening
- IAM/SG review
- backup/restore

## Semana 22 — Deploy strategies
- rolling
- blue-green
- canary (conceito)
- health checks
- rollback

## Semana 23 — Portfolio
O README final deve conter:
- objetivo
- arquitetura
- diagrama
- requisitos
- execução
- deploy
- variáveis
- segurança
- custos
- troubleshooting
- incidentes
- decisões técnicas
- limitações
- próximos passos

## Semana 24 — Interview / final gate
Treinar:
- “O que acontece quando digito uma URL?”
- “Como você investigaria um 502?”
- “Container vs VM?”
- “Security Group vs NACL?”
- “IAM user vs role?”
- “Por que Terraform?”
- “O que acontece quando um container morre?”
- “Como faria rollback?”
- “Como descobriria se o problema é DNS?”
- “Como você protege secrets?”

**Inglês**
- apresentar o projeto em 2 minutos
- explicar um incidente
- explicar uma decisão técnica
- responder perguntas comportamentais

---

# SISTEMA DE ESTUDO

Para cada tópico:

### 1. Understand
Leia documentação e entenda o modelo mental.

### 2. Build
Faça algo funcional.

### 3. Break
Quebre de propósito.

### 4. Diagnose
Investigue sem procurar a solução primeiro.

### 5. Recover
Corrija e valide.

### 6. Explain
Explique em voz alta.

### 7. Document
Registre o que aconteceu.

Se só fez o passo 1, **não marque como concluído**.

---

# DEFINIÇÃO DE COMPETÊNCIA

Use três estados:

- **SEI LER:** entendo documentação e conceitos.
- **SEI FAZER:** consigo executar sem tutorial.
- **SEI ME VIRAR:** consigo executar em ambiente desconhecido, diagnosticar quando falha e explicar a decisão.

O objetivo dos 6 meses é chegar ao terceiro estado nos tópicos CORE.

---

# ROTINA SEMANAL SUGERIDA

**5 sessões/semana**

- 2 × teoria/documentação
- 2 × laboratório
- 1 × troubleshooting + documentação

No fim da semana:

1. O que construí?
2. O que quebrei?
3. Como descobri a causa?
4. Como corrigi?
5. O que documentei?
6. Consigo explicar sem consultar?

---

# FONTES PRINCIPAIS

Priorize documentação oficial:

- AWS Docs — https://docs.aws.amazon.com/
- AWS Well-Architected — https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html
- Docker Get Started — https://docs.docker.com/get-started/
- Docker Docs — https://docs.docker.com/
- Terraform AWS Get Started — https://developer.hashicorp.com/terraform/tutorials/aws-get-started
- Terraform AWS Provider — https://registry.terraform.io/providers/hashicorp/aws/latest/docs
- GitHub Actions Quickstart — https://docs.github.com/en/actions/get-started/quickstart
- GitHub Actions — https://github.com/features/actions
- Prometheus — https://prometheus.io/docs/
- Grafana — https://grafana.com/docs/
- MDN HTTP — https://developer.mozilla.org/en-US/docs/Web/HTTP
- MDN DNS — https://developer.mozilla.org/en-US/docs/Glossary/DNS
- Linux man-pages — https://man7.org/linux/man-pages/
- Ubuntu Server Docs — https://documentation.ubuntu.com/server/
- Pro Git — https://git-scm.com/book/en/v2

---

# FINAL GATE — “OKAY, SEI ME VIRAR”

Você passa quando consegue, sem tutorial:

1. desenhar a arquitetura;
2. criar a infraestrutura;
3. acessar os servidores;
4. configurar serviços;
5. containerizar a aplicação;
6. fazer deploy;
7. automatizar o deploy;
8. observar o ambiente;
9. quebrar e diagnosticar;
10. recuperar;
11. explicar segurança e custos;
12. documentar;
13. apresentar tudo em inglês.

**Não precisamos saber tudo. Precisamos saber continuar quando não sabemos.**
