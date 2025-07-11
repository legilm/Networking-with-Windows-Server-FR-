Networking with Windows Server (FR)
Ce cours en classe de 5 jours fournit les compétences fondamentales en réseau nécessaires pour déployer et prendre en charge Windows Server dans la plupart des organisations.

La formation couvre les bases de l’IP, les technologies d’accès à distance et des contenus plus avancés, y compris le Software Defined Networking.

Bien que ce cours et les laboratoires associés soient conçus pour Windows Server 2022, les compétences enseignées seront également compatibles avec les versions antérieures de Server 2016 et Server 2019.

Content
Module 1 - Planification et mise en œuvre d'un réseau IPv4
Module 2 - Mise en œuvre du DHCP
Module 3 - Mise en œuvre d'IPv6
Module 4 - Mise en œuvre du DNS
Module 5 - Mise en œuvre de l'IPAM
Module 6 - Configuration de l'accès à distance dans Windows Server
Module 7 - Mise en œuvre de DirectAccess
Module 8 - Mise en œuvre des VPN
Module 9 - Mise en réseau des succursales
Module 10 - Mise en réseau des succursales
Module 11 - Mise en œuvre du Software Defined Networking
Learning Outcomes
Être en capacité d’installer, de configurer et d’administrer les services réseaux de Windows Server.
Training Method
Formation en présentiel, en français mais avec support de cours et environnement de labs en anglais.

# Classe A de Rede IPv4

- **Intervalo de endereços:** 1.0.0.0 a 126.255.255.255
- **Máscara padrão:** 255.0.0.0 (/8)
- **Quantidade de redes:** 128 (0 e 127 são reservados)
- **Hosts por rede:** Aproximadamente 16 milhões
- **Primeiro octeto:** 1 a 126
- **Uso:** Grandes organizações e redes com muitos dispositivos

**Exemplo de endereço Classe A:**  
`10.0.0.1`

> Observação: O endereço 127.0.0.0 é reservado para loopback (localhost).

# Classe B de Rede IPv4

- **Intervalo de endereços:** 128.0.0.0 a 191.255.255.255
- **Máscara padrão:** 255.255.0.0 (/16)
- **Quantidade de redes:** 16.384
- **Hosts por rede:** Aproximadamente 65 mil
- **Primeiro octeto:** 128 a 191
- **Uso:** Redes de médio porte, como universidades e grandes empresas

**Exemplo de endereço Classe B:**  
`172.16.0.1`

# Classe C de Rede IPv4

- **Intervalo de endereços:** 192.0.0.0 a 223.255.255.255
- **Máscara padrão:** 255.255.255.0 (/24)
- **Quantidade de redes:** 2.097.152
- **Hosts por rede:** 254
- **Primeiro octeto:** 192 a 223
- **Uso:** Pequenas redes, como redes domésticas e pequenas empresas

**Exemplo de endereço Classe C:**  
`192.168.1.1`

# Classes D e E

- **Classe D:** 224.0.0.0 a 239.255.255.255 — Reservada para multicast.
- **Classe E:** 240.0.0.0 a 255.255.255.255 — Reservada para uso futuro ou experimental.

> Observação: Classes D e E não são usadas para atribuição de endereços a hosts comuns.
# Endereços Classful vs. Classless

## Endereçamento Classful

O endereçamento classful foi o método original de atribuição de endereços IP, onde o espaço de endereços era dividido em classes fixas (A, B, C, D, E), cada uma com uma máscara de sub-rede padrão.

**Exemplo Classful:**
- Classe A: `10.0.0.0/8`
- Classe B: `172.16.0.0/16`
- Classe C: `192.168.1.0/24`

Neste modelo, a máscara de sub-rede era definida pela classe do endereço.

## Endereçamento Classless (CIDR)

O endereçamento classless, introduzido pelo CIDR (Classless Inter-Domain Routing), permite definir máscaras de sub-rede de qualquer tamanho, independentemente da classe do endereço. Isso proporciona maior flexibilidade e melhor utilização do espaço de endereços IP.

**Exemplo Classless:**
- `192.168.1.0/27` (sub-rede com 32 endereços)
- `10.0.0.0/12` (sub-rede maior que uma classe A padrão)
- `172.16.10.0/30` (sub-rede com apenas 4 endereços)

## Resumo

- **Classful:** Máscaras fixas baseadas na classe do endereço.
- **Classless:** Máscaras variáveis, definidas pelo administrador, usando notação CIDR (`/n`).

O modelo classless é o padrão atual, pois permite sub-redes mais eficientes e flexíveis.

# Lab: Planification d'un réseau IPv4 pour les succursales

## Scénario

A. Datum Corporation prévoit d'ouvrir trois succursales en Amérique du Nord : Houston, Mexico City et Portland. Vous devez planifier l'attribution des adresses IPv4 pour chaque succursale, en utilisant les plages d'adresses déjà assignées au bureau régional de Toronto. Les adresses pour les connexions filaires et sans fil doivent être distinctes.

## Répartition des équipements par succursale

## Plages d'adresses disponibles à Toronto

- **172.16.20.0/24 à 172.16.52.0/24** : Ordinateurs de bureau
- **172.16.53.0/24 à 172.16.60.0/24** : Appareils sans fil

## Plan d'attribution des sous-réseaux

### Houston

- **Appareils filaires (400 appareils)**
	- Sous-réseau requis : au moins 400 adresses utilisables
	- **Proposition** : 172.16.20.0/23 (512 adresses, 510 utilisables)
- **Appareils sans fil (150 appareils)**
	- Sous-réseau requis : au moins 150 adresses utilisables
	- **Proposition** : 172.16.53.0/24 (256 adresses, 254 utilisables)

### Mexico City

- **Appareils filaires (150 appareils)**
	- Sous-réseau requis : au moins 150 adresses utilisables
	- **Proposition** : 172.16.22.0/24 (256 adresses, 254 utilisables)
- **Appareils sans fil (70 appareils)**
	- Sous-réseau requis : au moins 70 adresses utilisables
	- **Proposition** : 172.16.54.0/25 (128 adresses, 126 utilisables)

### Portland

- **Appareils filaires (175 appareils)**
	- Sous-réseau requis : au moins 175 adresses utilisables
	- **Proposition** : 172.16.23.0/24 (256 adresses, 254 utilisables)
- **Appareils sans fil (225 appareils)**
	- Sous-réseau requis : au moins 225 adresses utilisables
	- **Proposition** : 172.16.55.0/24 (256 adresses, 254 utilisables)

## Résumé du plan d'adressage

| Succursale    | Filaire (subnet)      | Sans fil (subnet)      |
|---------------|----------------------|------------------------|
| Houston       | 172.16.20.0/23       | 172.16.53.0/24         |
| Mexico City   | 172.16.22.0/24       | 172.16.54.0/25         |
| Portland      | 172.16.23.0/24       | 172.16.55.0/24         |

> **Remarque :** Ce plan garantit que chaque type de connexion dispose de suffisamment d'adresses et que les plages sont distinctes pour les connexions filaires et sans fil.
# Definição de DirectAccess

O DirectAccess é um recurso do Windows Server que permite que computadores clientes estabeleçam automaticamente e de forma transparente uma conexão segura com a rede corporativa pela Internet, sem a necessidade de ação do usuário ou de uma VPN tradicional. O DirectAccess utiliza protocolos como IPv6, IPsec e tunelamento para fornecer acesso remoto contínuo aos recursos internos, mantendo a segurança e o gerenciamento centralizado dos dispositivos, mesmo quando estão fora do escritório.

# Roteamento (Routing)

O roteamento é o processo de encaminhar pacotes de dados entre redes diferentes, permitindo a comunicação entre dispositivos que não estão na mesma sub-rede. Em redes IP, os roteadores analisam o endereço de destino dos pacotes e determinam o melhor caminho para entregá-los ao destino final.

## Tipos de roteamento

- **Roteamento estático:** As rotas são configuradas manualmente pelo administrador. É simples, mas não se adapta automaticamente a mudanças na topologia da rede.
- **Roteamento dinâmico:** Os roteadores trocam informações entre si usando protocolos de roteamento, como RIP, OSPF ou BGP, ajustando as rotas automaticamente conforme necessário.

## Protocolos de roteamento comuns

- **RIP (Routing Information Protocol):** Protocolo simples, adequado para redes pequenas.
- **OSPF (Open Shortest Path First):** Protocolo mais avançado, usado em redes de médio e grande porte.
- **BGP (Border Gateway Protocol):** Utilizado para roteamento entre grandes redes, como na Internet.

## Exemplo de configuração de rota estática no Windows Server

```powershell
# Adiciona uma rota estática para a rede 192.168.10.0/24 via gateway 192.168.1.1
route add 192.168.10.0 mask 255.255.255.0 192.168.1.1
```

> O roteamento é fundamental para conectar diferentes segmentos de rede e garantir o fluxo eficiente de dados em ambientes corporativos.

# RADIUS Server e Proxy

## O que é um servidor RADIUS?

O RADIUS (Remote Authentication Dial-In User Service) é um protocolo utilizado para autenticação, autorização e contabilização (AAA) de usuários que acessam redes, como VPNs, Wi-Fi corporativo e conexões dial-up. No Windows Server, o serviço de RADIUS é implementado pelo NPS (Network Policy Server).

- **Autenticação:** Verifica as credenciais do usuário.
- **Autorização:** Define os privilégios de acesso.
- **Contabilização:** Registra informações sobre o uso da rede.

## Funcionamento do RADIUS

1. O cliente (por exemplo, um ponto de acesso Wi-Fi) encaminha as credenciais do usuário para o servidor RADIUS.
2. O servidor RADIUS valida as credenciais e retorna uma resposta de aceitação ou rejeição.
3. Se aceito, o usuário recebe acesso à rede conforme as políticas definidas.

## RADIUS Proxy

Um RADIUS Proxy encaminha solicitações de autenticação para outros servidores RADIUS, permitindo centralizar ou distribuir a autenticação entre diferentes domínios ou organizações.

- **Cenários comuns:**
	- Autenticação de usuários de diferentes domínios.
	- Roaming entre organizações (ex: eduroam).
	- Balanceamento de carga entre múltiplos servidores RADIUS.

## Exemplo de configuração básica no Windows Server

1. Instale o serviço NPS (Network Policy Server).
2. Configure clientes RADIUS (ex: pontos de acesso).
3. Defina políticas de rede para autenticação.
4. (Opcional) Configure o NPS como proxy para encaminhar solicitações a outros servidores RADIUS.

> O uso de RADIUS aumenta a segurança e o controle sobre o acesso à rede, sendo essencial em ambientes corporativos e educacionais.

# Network Policy Server (NPS) – Definição

O Network Policy Server (NPS) é o componente do Windows Server responsável por implementar políticas de autenticação, autorização e contabilização de acesso à rede, atuando como servidor RADIUS. O NPS permite centralizar o gerenciamento das políticas de acesso para conexões VPN, Wi-Fi corporativo, autenticação 802.1X e outros métodos de acesso remoto.

## Principais funções do NPS

- **Servidor RADIUS:** Autentica e autoriza solicitações de acesso à rede.
- **Proxy RADIUS:** Encaminha solicitações para outros servidores RADIUS.
- **Gerenciamento de políticas:** Define regras baseadas em grupos, horários, localizações, tipos de conexão e outros critérios.
- **Contabilização:** Registra logs detalhados sobre tentativas de acesso e uso da rede.

## Benefícios

- Centralização das regras de acesso à rede.
- Integração com o Active Directory para autenticação de usuários.
- Suporte a autenticação forte (EAP, PEAP, certificados).
- Auditoria e relatórios de acesso.

> O NPS é essencial para ambientes que exigem controle rigoroso e seguro sobre quem pode acessar a rede e sob quais condições.

# Certificados

CA (Certificate Authority / Autoridade Certificadora):
É uma entidade confiável responsável por emitir, validar e revogar certificados digitais. Ela garante que o certificado realmente pertence à entidade (usuário, computador, servidor) que diz possuir.

PKI (Public Key Infrastructure / Infraestrutura de Chave Pública):
É o conjunto de tecnologias, políticas e procedimentos que permitem a criação, gerenciamento, distribuição, uso, armazenamento e revogação de certificados digitais e chaves criptográficas. A PKI utiliza CAs para garantir a confiança nas identidades digitais.

Certificado Digital:
É um arquivo eletrônico que associa uma chave pública a uma identidade (pessoa, computador, serviço), permitindo autenticação e comunicação segura.

Chave Pública e Chave Privada:
São pares de chaves criptográficas. A chave pública é distribuída e pode ser compartilhada; a chave privada é mantida em segredo pelo proprietário.

Esses conceitos são fundamentais para autenticação forte, como em redes Wi-Fi corporativas usando EAP-TLS, onde o NPS valida certificados emitidos por uma CA confiável dentro de uma PKI.

# RRAS, Routing e NAT no Windows Server

## O que é RRAS?

O RRAS (Routing and Remote Access Service) é um serviço do Windows Server que permite que o servidor atue como roteador, servidor VPN e forneça acesso remoto seguro à rede corporativa. Com o RRAS, é possível implementar roteamento entre sub-redes, NAT (Network Address Translation) e conexões VPN para usuários remotos.

## Funcionalidades principais do RRAS

- **Roteamento IP:** Permite que o servidor encaminhe pacotes entre diferentes redes/sub-redes.
- **NAT (Network Address Translation):** Permite que múltiplos dispositivos em uma rede interna acessem a Internet usando um único endereço IP público.
- **Servidor VPN:** Oferece acesso remoto seguro à rede via protocolos como PPTP, L2TP, SSTP e IKEv2.
- **Acesso Dial-up:** Suporte a conexões discadas (menos comum atualmente).

## Configuração básica de roteamento com RRAS

1. Instale o serviço RRAS via Gerenciador de Servidores ou PowerShell.
2. Configure o RRAS para atuar como roteador (roteamento LAN-LAN) ou servidor VPN.
3. Adicione interfaces de rede correspondentes às sub-redes que deseja rotear.
4. (Opcional) Configure rotas estáticas ou dinâmicas conforme necessário.

## NAT com RRAS

O NAT permite que dispositivos de uma rede privada acessem recursos externos (como a Internet) usando um único endereço IP público. O RRAS pode ser configurado para atuar como gateway NAT:

- **Interface pública:** Conectada à Internet (IP público).
- **Interface privada:** Conectada à rede interna (IP privado).
- O RRAS traduz os endereços IP internos para o endereço público ao encaminhar pacotes para a Internet.

### Exemplo de configuração de NAT no RRAS

1. No Gerenciador de Servidores, adicione a função "Serviço de Acesso Remoto" e selecione "Roteamento e Acesso Remoto".
2. Abra o console RRAS, clique com o botão direito no servidor e escolha "Configurar e habilitar RRAS".
3. Selecione "NAT personalizado" ou "NAT com acesso à Internet".
4. Defina a interface conectada à Internet como pública e habilite NAT nela.
5. Defina a interface interna como privada.

> O RRAS é uma solução versátil para roteamento, NAT e acesso remoto em ambientes Windows Server, facilitando a integração de redes e o acesso seguro de usuários remotos.


# Web Application Proxy – Definição

O Web Application Proxy (WAP) é uma função do Windows Server que atua como um gateway reverso, permitindo que usuários externos acessem aplicações web internas de forma segura. Ele faz parte do serviço de Acesso Remoto e é frequentemente utilizado para publicar aplicações como o Exchange, SharePoint ou portais internos, protegendo-os com autenticação adicional, como o Active Directory Federation Services (AD FS).

## Principais funções do Web Application Proxy

- **Publicação segura de aplicações web internas para usuários externos**
- **Autenticação prévia** dos usuários antes de permitir o acesso às aplicações
- **Integração com AD FS** para autenticação baseada em claims e Single Sign-On (SSO)
- **Proteção contra ameaças externas** ao não expor diretamente os servidores internos

## Benefícios

- Permite acesso remoto seguro a aplicações corporativas
- Suporte a autenticação multifator e políticas de acesso condicional
- Reduz a superfície de ataque da rede interna

> O Web Application Proxy é essencial para organizações que precisam fornecer acesso remoto seguro a aplicações web internas, mantendo o controle e a segurança dos recursos corporativos.

# DFS (Distributed File System) – Definição

O DFS (Distributed File System) é um conjunto de serviços do Windows Server que permite organizar, gerenciar e compartilhar pastas e arquivos distribuídos em múltiplos servidores de forma centralizada e transparente para os usuários. Com o DFS, é possível criar um namespace unificado, facilitando o acesso e a redundância dos dados.

## Principais componentes do DFS

- **DFS Namespaces:** Permite criar uma estrutura lógica de pastas (namespace) que pode apontar para compartilhamentos em diferentes servidores, apresentando um caminho único para os usuários.
- **DFS Replication:** Sincroniza automaticamente arquivos e pastas entre servidores, garantindo alta disponibilidade e tolerância a falhas.

## Benefícios

- Acesso simplificado a arquivos, independentemente da localização física.
- Redundância e alta disponibilidade por meio de replicação.
- Balanceamento de carga e otimização do acesso em ambientes distribuídos.

> O DFS é amplamente utilizado para centralizar o acesso a arquivos em organizações com múltiplas filiais ou servidores, melhorando a resiliência e a experiência do usuário.

# BranchCache – Definição

O BranchCache é um recurso do Windows Server que otimiza o uso da largura de banda WAN em filiais (branch offices) ao armazenar em cache localmente o conteúdo acessado de servidores centrais. Quando um usuário em uma filial solicita um arquivo ou conteúdo de um servidor central, o BranchCache armazena uma cópia localmente. Solicitações subsequentes ao mesmo conteúdo são atendidas a partir do cache local, reduzindo o tráfego WAN e acelerando o acesso.

## Modos de operação

- **Modo Distribuído:** O cache é armazenado nos próprios computadores clientes da filial.
- **Modo Hospedado:** O cache é centralizado em um servidor dedicado na filial.

## Benefícios

- Reduz o consumo de banda WAN entre matriz e filiais.
- Melhora o tempo de resposta para acesso a arquivos e conteúdos repetidos.
- Transparente para o usuário final e fácil de gerenciar via políticas de grupo.

> O BranchCache é ideal para organizações com múltiplas filiais que acessam frequentemente arquivos ou aplicações hospedadas em datacenters centrais.

# NIC Timing – Definição

NIC Timing refere-se ao tempo e à sincronização envolvidos nas operações de uma placa de interface de rede (Network Interface Card – NIC). Isso inclui o tempo necessário para processar pacotes, responder a sinais de rede e coordenar a transmissão e recepção de dados. Um bom gerenciamento de timing na NIC é essencial para garantir baixa latência, alta taxa de transferência e comunicação eficiente entre dispositivos de rede.

## Aspectos importantes do NIC Timing

- **Latência:** Tempo entre o envio de um pacote e sua recepção.
- **Buffering:** Gerenciamento de filas de pacotes para evitar perda de dados.
- **Clock interno:** Sincronização precisa para transmissão de dados em redes de alta velocidade.
- **Offloading:** Algumas NICs realizam tarefas como checksum ou segmentação para otimizar o desempenho e reduzir a carga da CPU.

> O ajuste e monitoramento do timing da NIC são especialmente importantes em ambientes de data center, virtualização e aplicações sensíveis à latência, como VoIP e trading financeiro.


# SMB 3.1.1 – Definição

O SMB (Server Message Block) 3.1.1 é a versão mais recente do protocolo SMB, introduzida no Windows 10 e Windows Server 2016. Ele é utilizado para compartilhamento de arquivos, impressoras e outros recursos de rede entre computadores Windows e sistemas compatíveis.

## Principais recursos do SMB 3.1.1

- **Segurança aprimorada:** Suporte a criptografia AES-128-GCM e AES-128-CCM para proteger dados em trânsito.
- **Pré-autenticação de integridade:** Garante que a sessão SMB não seja comprometida antes da autenticação, protegendo contra ataques de downgrade.
- **Negociação segura:** Utiliza algoritmos mais robustos para negociar capacidades entre cliente e servidor.
- **Desempenho otimizado:** Suporte a múltiplos canais, compressão de dados e melhorias em ambientes de virtualização e datacenter.

## Benefícios

- Maior proteção contra ataques de interceptação e manipulação de dados.
- Compatibilidade com recursos avançados de armazenamento e alta disponibilidade.
- Melhor desempenho em redes modernas.

> O SMB 3.1.1 é recomendado para ambientes que exigem alta segurança e desempenho no compartilhamento de arquivos e recursos em redes Windows.

# RSS (Receive Side Scaling) no SMB

O RSS (Receive Side Scaling) é uma tecnologia de otimização de rede suportada pelo Windows Server e utilizada pelo protocolo SMB para melhorar o desempenho do tráfego de rede em servidores com múltiplos processadores ou núcleos.

## Como funciona o RSS

O RSS distribui o processamento dos pacotes de rede recebidos entre vários núcleos de CPU, evitando que todo o tráfego seja tratado por um único núcleo. Isso reduz gargalos, melhora a escalabilidade e aumenta a taxa de transferência em ambientes de alto desempenho, como servidores de arquivos que utilizam SMB 3.x.

## Benefícios do RSS no SMB

- **Melhor uso dos recursos do servidor:** Distribui a carga de trabalho de rede entre múltiplos núcleos.
- **Aumento do throughput:** Permite maior volume de dados transferidos simultaneamente.
- **Redução de latência:** Minimiza atrasos no processamento de pacotes SMB.

> O RSS é especialmente importante em servidores com múltiplas conexões SMB, como ambientes de virtualização, clusters e datacenters, garantindo desempenho consistente e eficiente no acesso a arquivos e recursos compartilhados.

# SR-IOV – Definição

SR-IOV (Single Root I/O Virtualization) é uma tecnologia que permite que uma única placa de interface de rede física (NIC) seja compartilhada diretamente entre múltiplas máquinas virtuais (VMs), proporcionando acesso quase nativo ao hardware. Com SR-IOV, a NIC é dividida em múltiplas interfaces virtuais chamadas de Virtual Functions (VFs), que podem ser atribuídas individualmente às VMs.

## Benefícios do SR-IOV

- **Desempenho elevado:** Reduz a sobrecarga de virtualização, oferecendo baixa latência e alta taxa de transferência.
- **Menor uso da CPU:** O tráfego de rede é processado diretamente pela NIC, minimizando a intervenção do hypervisor.
- **Isolamento:** Cada VM tem sua própria interface virtual, aumentando a segurança e a separação do tráfego.

## Cenários de uso

SR-IOV é amplamente utilizado em ambientes de virtualização que exigem alto desempenho de rede, como datacenters, servidores de arquivos e aplicações sensíveis à latência.

> O suporte a SR-IOV depende tanto do hardware da NIC quanto do hypervisor e do sistema operacional utilizados.
# SDN (Software Defined Networking) – Definição

SDN (Software Defined Networking) é uma abordagem de rede que separa o plano de controle (responsável pelas decisões de roteamento e políticas) do plano de dados (responsável pelo encaminhamento efetivo dos pacotes). Em vez de depender de dispositivos de rede tradicionais com controle distribuído, o SDN centraliza a inteligência de rede em um controlador de software, permitindo configuração, automação e gerenciamento dinâmico da infraestrutura de rede.

## Principais características do SDN

- **Centralização do controle:** Um controlador SDN gerencia toda a rede, facilitando a aplicação de políticas e mudanças de configuração.
- **Programabilidade:** A rede pode ser configurada e automatizada via APIs, scripts ou ferramentas de orquestração.
- **Flexibilidade:** Permite rápida adaptação a novas demandas, como segmentação de rede, provisionamento de serviços e balanceamento de carga.
- **Visibilidade:** Proporciona monitoramento centralizado e detalhado do tráfego e do desempenho da rede.

## Benefícios

- Redução da complexidade operacional e dos custos de gerenciamento.
- Maior agilidade para implementar novas políticas e serviços.
- Facilidade de integração com ambientes de nuvem, virtualização e automação.

> O SDN é fundamental em datacenters modernos, redes corporativas e ambientes de nuvem, permitindo redes mais ágeis, seguras e eficientes.

# NVGRE – Definição

NVGRE (Network Virtualization using Generic Routing Encapsulation) é uma tecnologia de virtualização de rede desenvolvida pela Microsoft para permitir a criação de redes virtuais sobre uma infraestrutura física compartilhada. Utilizando o protocolo GRE para encapsular pacotes, o NVGRE permite que múltiplas redes virtuais coexistam de forma isolada, mesmo utilizando o mesmo espaço de endereçamento IP.

## Principais características do NVGRE

- **Encapsulamento GRE:** Os pacotes de rede das máquinas virtuais são encapsulados em pacotes GRE, permitindo o transporte transparente sobre a rede física.
- **Isolamento de redes:** Permite que diferentes clientes ou departamentos utilizem o mesmo intervalo de endereços IP sem conflitos.
- **Escalabilidade:** Facilita a criação de milhares de redes virtuais em ambientes de nuvem e datacenter.
- **Integração com SDN:** Pode ser gerenciado por controladores SDN para automação e orquestração de redes virtuais.

## Benefícios

- Simplifica a mobilidade de máquinas virtuais entre hosts físicos.
- Reduz a complexidade de configuração de VLANs tradicionais.
- Suporta ambientes multi-tenant com isolamento seguro.

> O NVGRE é utilizado principalmente em ambientes de virtualização e nuvem, sendo uma das tecnologias base para redes definidas por software (SDN) no Windows Server.

# SLB (Software Load Balancer) – Definição

O SLB (Software Load Balancer) é um componente do Windows Server e do SDN que distribui automaticamente o tráfego de rede entre múltiplos servidores ou serviços, garantindo alta disponibilidade e escalabilidade das aplicações. Diferente dos balanceadores de carga tradicionais baseados em hardware, o SLB é implementado por software e integrado à infraestrutura virtualizada.

## Principais características do SLB

- **Balanceamento de carga Layer 4 (TCP/UDP):** Distribui conexões de rede de forma eficiente entre instâncias de serviço.
- **Alta disponibilidade:** Redireciona o tráfego automaticamente em caso de falha de um servidor.
- **Escalabilidade dinâmica:** Permite adicionar ou remover servidores sem interromper o serviço.
- **Integração com SDN:** Gerenciado centralmente pelo controlador SDN, facilitando automação e orquestração.

## Benefícios

- Reduz pontos únicos de falha e melhora a resiliência das aplicações.
- Otimiza o uso dos recursos de rede e servidores.
- Facilita a implantação de aplicações em ambientes de nuvem e datacenter.

> O SLB é essencial para garantir desempenho, disponibilidade e flexibilidade em ambientes modernos baseados em Windows Server e redes definidas por software.