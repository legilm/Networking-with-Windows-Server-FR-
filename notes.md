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