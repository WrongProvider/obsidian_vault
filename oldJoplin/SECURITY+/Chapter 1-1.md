Chapter 1

# **Use cases**

1.  actors
2.  precondition
3.  trigger
4.  postcondition
5.  normal flow
6.  alternate flow

# Ensure confidentiality

## Encryption

AES

## Access control

1.  Identification
2.  authentication
3.  autorization

### Remember

confidencialidade eh algo que garante que os dados vão ser usados somente por pessoas autorizadas, encriptação de dados, como PII, banco de dados e dispositivos móveis. Access control ajuda a proteger a confidencialidade, restringindo acesso.

# Provide Integrity

## garante que os dados não mudaram

### Remember

secure hash algorith (SHA) -> output irreversivel e fixo. Caso o hash seja diferente o arquivo mudou.

É importante dizer que não da pra saber qual parte foi modificada.

md5sum.exe to calculate md5 hashes

hash sempre verificar os hashes de arquivos

# **Increase Availability**

preciso atender a demanda em um determinado tempo

## Redundancy and Fault Tolerance

Redundancy adiciona duplicacao critica a sistemas, providenciando fault lolerance.

Objetivo: remover todo **single point of failure (SPOF), se o SPOF falha o sistema inteiro falha.**

**ex: ter apenas um disco. É um SPOF**

- disk redundancies:
    - raid-1 (mirroring), raid-5 (striping with parity), raid-10 (striping with a mirror)
- server redundancies
    - failover clusters incluem serves redundantes, garantindo a continuidade do servidor,
    - virtualizacao tb é usada
- network redundancies
    - load balancing
    - power redundancies:  Uninterruptible power supplies (UPSs) and power generators

Remember:

Disponibilidade garante que os sistemas estao up e operacionais quando necessarios, e muitos abordam (leva em consideração) SPOF.

## **Scalability and Elasticity**

**Scalability: capacidade de escalar um sistema (up and down), o opnto aqui é que essa escalabilidade é feita manualmente**

**Elasticity: capacidade de escalar um sistema dinamicamente, quando pintar necessidade. Lembra de cloud**

## **Patching**

**sempre deixar o sistema atualizado para correções de bugs (patch management)**

**Remember**

# **Understanding Resiliency**

**É possível ter 99.999 % uptime porém isso requer a eliminação de todos SPOF e adicionar multiplas redundancias.**

**Isso aumenta o TCO (total cost of ownership) significativamente**

\*\*Reliency methods \*\*ajudam sistemas a se curar sozinhos após falhas com o minimo de downtime.

Por exemplo um sistema de resiliencia usa metodos de alta disponibilidade, performando testes full backups, ter backup em power sources, NICs, ou discos redundantes.

Espera que componentes retestem os processos falhados.

Pensa no protocolo TCP (sempre pede pra reenviar caso não receba)

# Resource Versus Security Constraints

imagine que o CISO fala que é legal encriptar os dados do DB, e nisso precisaria de mais 40% de capacidade de disco, o que leva a empresa a investir em mais recursos e até trazendo lentidão ao serviço. É preciso ter um meio termo.

# Introduncing Basic Risk Concepts

**Risk:** eh a possibilidade de uma ameaça explorar uma vulnerabilidade resultando em perdas.

**Threat:** qualquer evento que possa comprometer a triade (integridade, confidencialidade e disponibilidade)

**Vulnerabilidade:** eh uma fraqueza, algo a ser explorado

**Security Incident:** eh um evento ou conjunto de eventos adversos que afentam negativamente a CIA (triade) dos sistemas de informacao da organizacao.

**Risk mitigation:** reduz a chance de uma Threat explorar uma Vulnerabilidade. Da pra reduzir riscos implementado controles. (countermeasures and safeguards). Remeber vc n pode prever a maioria das ameaças (tornado, furacao etc) mas reduzir o risco, diminuindo vulnerabilidades ou o threat's impact

**Remember** this Risk is the likelihood that a threat will exploit a vulnerability. Risk mitigation reduces the chances that a threat will exploit a vulnerability or reduces the risk’s impact by implementing security controls.

# Understanding Security Controls

- **Managerial Controls**
    - Mais administrativos em funcao. São tipicamente documentados na politica de seguranca da organizacao e foca em gerenciar riscos.
- **Operational Controls**
    - ajuda a garantir que a operacao do dia-a-dia da organizacao esteja em compliance com a politica de seguranca. Pessoas implementam ela.
- **Technical Controls**
    - usa de hardware, software e firmware para reduzir vulnerabilidades

**Remember**: documented in written policies, permormed in d2d operations or implemented with tecnology

CompTIA also lists the following control types in the objectives:

- **Preventative controls** attempt to prevent an incident from occurring.
- **Detective controls** attempt to detect incidents after they have occurred.
- **Corrective controls** attempt to reverse the impact of an incident.
- **Deterrent controls (controle de dissuasão)** attempt to discourage individuals from causing an incident.
- **Compensating controls** are alternative controls used when a primary control is not feasible.
- **Physical controls** refer to controls you can physically touch.

NIST and SP 800 Documents

https://csrc.nist.gov/publications/PubsSPs.html.

# Managerial Controls

- **Risk assessment:** quantifica e qualifica os riscos, para focar nos piores
- **Vulnerability assessments:** Tenta descobrir vulnerabilidades, e quando necessário, controles adicionais são usados para reduzir os riscos dessas vulnerabilidades.

# Operational Controls

- **Awareness and Training:** a importancia do treinamento de reduzir riscos não pode ser subestimanda, ajuda a manter segurança de senhas, clean desk policy, e enteder phishing, malware etc.
- **Configuration management:** usa baselines para garantir que sistemas estejam em um estado hardened e seguro. Ver change managemnet
- **Media Protection:** USB, drives, etc
- **Physical and environmental protection:** mantrap, cameras, door locks.

remember: feito por pessoas no dia a dia operacional. Entrando em compliance com a politica de segurnaçá da empresa.

# Technical Controls

- **Encryption:** protege a confidencialidade, presente em dados, computadores, mobile
- \*\*antivirus software: \*\*protecao contra malware
- \*\*IDS (intrusion detection system) e IPS (intrusion prevention system): \*\*podem monitorar um rede ou um host esperando intrusoes e providencia protecao a varias threats.
- \*\*Firewalls: \*\*restringe trafego interno e externo.
- \*\*Least privilege: \*\*esse principio especifica que individuos ou processos são garantidos apenas os privilegios necessarios para performar tasks ou functions.

**Remember: esses caras reduzem vulnerabilidades através de software, IDSs, IPSs, firewall etc. Hardware: motion detections, fire suppression systems**

# **Control Types**

controles designados para performar funcoes relacionadas a incidentes de seguranca. Algumas classificações são: preventative, detective, corrective, deterrent, compensating e physical. Vai ver um crossover entre as categorias.

## Preventative

controles de prevencao

- \*\*Hardening: \*\*pratica para fazer um sistema ou aplicacao mais segura que sua configuracao default. Usam uma defense-in-depth strategy com uma seguranca em camadas. Que incluem: desabilitar portas e serviços desnecessarios, manter o patch, implementar protocolos seguros, senhas e politicas, desabilitar contas desnecessarias.
- \*\*Training: \*\*Garantir que os usuários estão cientes de vulnerabilidades e ameacas, para previnir incidentes. Social engeneering
- **Security Guards:** seguranca contra acesso nao autorizado do predio, previne egenheria social
- \*\*Change Management: \*\*garante que mudancas não vao resultar em interrupcoes nao intencionais. É um controle operacional, e tenta previnir incidentes. É tanto **operational control** quanto um **preventative.**
- \*\*Account disablement policy: \*\*garante que as contas são desabilitadas (antigas)
- \*\*IPS: \*\*block em tráfego malicioso antes que chegue na rede.

## **Detective Control**

- \*\*Log monitoring: \*\*record de logs
- \*\*Security information and event management (SIEM) systems: \*\*usa do SIEM para detectar trends e realizar alertas em tempo real
- \*\*Security audit: \*\*pode examinar a postura de seguraça da organizacao. Por exemplo um account audit para determinar se politicas tecnicas e pessoais estão sendo implementadas corretamente
- \*\*Video surveillance: \*\*a closed-circuit (CCTV) pode gravar eventos fisicos que ocorreram
- **Motion detection:** alarms
- \*\*Intrusion detection system (IDS): \*\*detecta trafego malicioso.

## Corretive and recovery controls

- \*\*Backup and system recovery: \*\*garante que dados podem ser restaurados
- \*\*Incident handling processes: \*\*handle incidents, incident response policy e incident response plan

## Physical Controls

bollands, barricades, access control vestibules (mantraps) lighting, signs, fences, sensors and more. Alguns podem ser tambem **preventive** and \*\*deterrent \*\*como os cadeados.

## Deterrent Controls

usado para desencorajar atacantes

- \*\*Cable locks: \*\*lock no cabo para não permitir roubo de laptop por ex
- **Physical locks:** locked doors, securing a wiring closet ou um server room.

## Compensating Controls

literalemnte a palavra, caso o funcionario não tenha ainda o SMART card para autenticar, no caso de novos funcionarios, a organizacao pode escolher implementar uma Time-based One-time password (TOTP) -- o da a organizacao ainda uma boa seguranca.

## Response Controls

response controls ou incident response controls, são feitos para preparar para incidentes de seguraça e responder quando eles ocorrem. Esses tipicamente comecam com politicas de segurança seguido de treinamento pessoal em como responder a incidentes.

# Combining Control Categories and Types

na prova, eles combinam esses tipos, então por isso encriptacao pode ser preventative technical control -> (pois previne rouvo de dados, e voce pode implementar com tecnologia.

similarmente a fire suppression system is a physical technical control -> é fisico porem tem tecnologia para detectar e extinguir fogos.

# Using Command-Line Tools

## Network Reconnaissance and Discovery

gcgapremium.com/501-extras

labs sobre

ping -t windows

ping -c linux (imita o windows)

use ping para checar name resolution

## Beware of Firewalls

reply time out

remember DoS usa  ICMP e pode barrar etc

ping, hping

ipconfig e ifconfig

ipconfig /displaydns

ipconfig /flushdns

net**-tools package:**

ifconfig eth0

ifconfig eth0 promisc -> processa todo o trafego que ve

ifconfig eth0 allmulti -> enable multicast

ifconfig eth0 -allmulti > disable

config com o novo ip:

ip link show -> show int

ip link set eth0 up -> enable

ip -s link -> statistics

netstat tcp

netstat -a tcp e udp

netstat -r routing table

netstat -e statistics

\- s protocol statistcs

-n numerical

-p &lt;protocol&gt; estaticas de um protocolo

combinacao -anp tcp (all numbered for tcp)

tracert and traceroute

hop RTT (round trip times)

tracert -d nao resolve dns

pathping -n (not domain) otimo para troubleshoot intermediario (problema interno na rota) so existe em windows

no linux é mtr

arp

arp -a

arp -a &lt;ip&gt;

# Linux and LAMP

Linux apache, MySQL, php, peal ou python

## Comands

sudo **cat** /var/log/auth.log -> eventos de auth

sudo **grep** "authentication failure"/var/log/auth.log

head

tail -n 15

logger backup started -> em /var/log/syslog vai aparecer a mensagem -- otimo para logar coisas

journalctl --since "1 hour ago"

journalctl --list-boots -> mostra logs do boot

journalctl -1

journalctl -- since "1 hour ago"> myjournal.txt

chmod -> RWX OGE (read write exec | owner group everyone) 1 -> exec, 2-> read, 4 -> write

chmod g=r (group = read | o-x tira o executavel de todos os outros) u -> file owner, g -> group owner, o-> others

## Event Viewer WINDOWS logs

Security log

It records auditable events such as successes or failures. Success indicates an audited event completed successfully, such as a user logging on or successfully deleting a file. Failure means that a user tried to perform an action but failed, such as failing to log on or attempting to delete a file but receiving a permission error instead. Windows enables some auditing by default, but administrators can add additional auditing..

System

The operating system uses the System log to record events related to the functioning of the operating system. This can include when it starts, when it shuts down, information on services starting and stopping, drivers loading or failing, or any other system component event deemed important by the system developers.

Application Log

The Application log records events sent to it by applications or programs running on the system. Any application has the capability of writing events in the Application log. This includes warnings, errors, and routine messages.

## Network logs

logs padrao do w3c:

**host**: The IP address or hostname of the client requesting the page.

**user-identifier:** The name of the user requesting the page (if known)

**authuser**: The logon name of the user requested in the page, if the user logged on.

**date**: The date and time of the request.

**request**: The actual request line sent by the client.

**status**: The HTTP status code returned to the client

**bytes**: The byte length of the reply.

# Centralized log Methods

SIEM Systems

combina o SEM (security information management) e o SIM (security information management)

log collectors: coleta logs (agents) e armazena em um db

data inputs: sources de logs vem de firewalls, router, NIDs etc

log aggregation: agrega log a um lugar que eh facil de analizar e procurar.

correlation engine: um software que coleta e analiza eventos de varios systemas. (geralmente ver common attributes)

Reports: reporta os trafegos, eventos etc

Packet Capture: analise de tráfegos

User behavior analysis: foca onde, e o que o usuário está fazendo, que aplicacao esta usando etc.

Sentiment analysis: analise de sentimento, comportamental

Security monitoring: monitora e notifica

Automated triggers: se um atacante errar o SSH 5x ele muda o ambiente para parar o ataque.

Time synchronization: sincroniza o tempo, todo mundo para GMT

Event deduplication: remove duplicatas

Logs/WORM: tem protecao contra edicao de logs, write once read many.

E para quem tem o NOC (network operation center) num grande display:

Sensors: muitos sistemas de SIEM usam agents pegos em systemas.

Alerts: quando bate um evento gera um alerta

Sensitivity: limitar falsos positivos e negativos

Correlation: faz a correlacao e analise dos dados

Trends: pode identificar trends

# Syslog

rfc 5424

muitas das syslogs vao para o /var/syslog e da pra mexer na conf em /etc/syslog.conf

514 UDP e 6514 (TCP com TLS) -> a segunda sendo a mais segura

## Syslog-ng and Rsyslog

mais velha e mais nova

## NXlog

funciona como um log collector e pode ser integrado com a maioria dos SIEMs, tem duas versoes: uma comunity e outra enterprise

# Syslogs

/var/log/auth.log -> logs de auth

/syslog -> armazena qualquer atividade do systema

/messages -> mensagens de logs que ocorrem durante o startup, mail, kernel e auth.

/boot.log -> boot

/faillog -> failed login attempts, da pra usar o failog command

/kern.log -> kernel

/httpd/ -> apache

# Chapter 1 Exam Topic Review