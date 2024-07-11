# Atividade de Segurança de Informação

## 1. O que é a arquitetura de segurança OSI?

A arquitetura de segurança OSI (Open Systems Interconnection) refere-se a um modelo conceitual que descreve como diferentes camadas de um sistema de comunicação devem interagir entre si para garantir a segurança das informações que estão sendo transmitidas. O modelo OSI é dividido em várias camadas, cada uma com funções específicas, e a arquitetura de segurança OSI se preocupa em garantir a segurança em todas essas camadas.

As camadas do modelo OSI incluem:

- **Camada Física:** Esta camada lida com a transmissão física dos dados, como a transmissão de bits através de cabos ou ondas de rádio.
- **Camada de Enlace de Dados:** Responsável pela comunicação entre dispositivos adjacentes na rede e pela detecção e correção de erros que possam ocorrer durante a transmissão.
- **Camada de Rede:** Esta camada lida com o roteamento dos dados através da rede, garantindo que eles cheguem ao destino correto.
- **Camada de Transporte:** Responsável pela entrega confiável dos dados, incluindo a segmentação dos dados em pacotes menores, se necessário, e a reordenação e retransmissão desses pacotes, se ocorrerem erros.
- **Camada de Sessão:** Esta camada estabelece, gerencia e encerra as conexões entre os sistemas em comunicação.
- **Camada de Apresentação:** Responsável pela formatação e criptografia dos dados para garantir que eles sejam compreendidos pelo destinatário.
- **Camada de Aplicação:** A camada mais próxima do usuário final, responsável por fornecer serviços de rede aos aplicativos do usuário.

## 2. Qual é a diferença entre ameaças à segurança passivas e ativas?

As ameaças à segurança passivas e ativas representam diferentes abordagens que os atacantes podem adotar para comprometer a segurança de sistemas, redes e dados. Aqui está a diferença entre elas:

### Ameaças Passivas:
- As ameaças passivas são geralmente caracterizadas por tentativas de acesso não autorizado ou observação de informações sem alterá-las.
- Um exemplo comum de ameaça passiva é a interceptação de dados durante a transmissão através de uma rede, como o monitoramento de comunicações não criptografadas.
- Outro exemplo seria a coleta de informações sensíveis por meio de técnicas de engenharia social, como a observação de informações confidenciais em locais públicos.
- As ameaças passivas visam obter informações sem que o usuário ou o sistema afetado perceba a violação.

### Ameaças Ativas:
- As ameaças ativas envolvem ações diretas destinadas a comprometer a integridade, disponibilidade ou confidencialidade dos sistemas, redes ou dados.
- Isso pode incluir atividades como ataques de negação de serviço (DoS) ou ataques de força bruta para tentar quebrar senhas.
- Outros exemplos de ameaças ativas incluem malware que modifica ou corrompe dados, como vírus, worms e cavalos de Troia, além de ataques de injeção de código, como SQL injection, que visam manipular bancos de dados.
- As ameaças ativas geralmente exigem interação direta com o sistema-alvo e têm o potencial de causar danos significativos ou interrupções.

## 3. Liste e defina resumidamente as categorias de ataques passivos e ativos à segurança.

### Ataques Passivos:

- **Interceptação de Dados:** Captura e análise de dados transmitidos pela rede, geralmente sem conhecimento do usuário.
- **Monitoramento de Tráfego:** Observação do tráfego de rede para extrair informações sobre padrões de comunicação, fluxo de dados e outros detalhes que possam ser explorados.
- **Reconhecimento de Rede:** Coleta de informações sobre a topologia da rede, dispositivos conectados e serviços em execução para identificar pontos fracos e possíveis alvos.
- **Engenharia Social:** Manipulação psicológica de pessoas para obter informações confidenciais, como senhas ou detalhes de acesso, sem recorrer a técnicas técnicas avançadas.

### Ataques Ativos:

- **Negação de Serviço (DoS):** Sobrecarregamento de recursos de sistema ou rede para tornar serviços indisponíveis para usuários legítimos.
- **Injeção de Código:** Introdução de código malicioso em sistemas ou aplicativos para explorar vulnerabilidades e executar ações não autorizadas.
- **Exploração de Vulnerabilidades:** Aproveitamento de falhas de segurança conhecidas em sistemas ou aplicativos para ganhar acesso não autorizado ou comprometer a integridade dos dados.
- **Ataques de Man-in-the-Middle (MitM):** Interposição em comunicações entre duas partes legítimas para interceptar e possivelmente modificar dados transmitidos.
- **Ataques de Sniffing:** Monitoramento passivo de tráfego de rede para capturar dados sensíveis, como senhas ou informações de login.

## 4. Liste e defina resumidamente as categorias dos serviços de segurança.

- **Firewall:** Um firewall é um dispositivo ou software que controla o tráfego de rede entre redes confiáveis e não confiáveis, aplicando regras de segurança para bloquear ou permitir o tráfego com base em políticas predefinidas.
- **Antivírus/Antimalware:** Esses serviços buscam identificar, bloquear e remover programas maliciosos, como vírus, worms, cavalos de Troia e spyware, que possam comprometer a segurança dos sistemas.
- **Sistema de Detecção e Prevenção de Intrusões (IDS/IPS):** O IDS monitora o tráfego de rede ou atividades do sistema em busca de padrões suspeitos que possam indicar uma violação de segurança, enquanto o IPS pode agir automaticamente para bloquear ou prevenir atividades maliciosas.
- **VPN (Virtual Private Network):** Uma VPN cria uma conexão segura e criptografada entre dispositivos ou redes através de uma rede pública, permitindo que os usuários acessem recursos de rede de forma segura, mesmo em redes não confiáveis, como a internet.
- **Controle de Acesso:** Esses serviços garantem que apenas usuários autorizados tenham acesso aos recursos de rede e dados, utilizando autenticação, autorização e políticas de acesso para gerenciar privilégios de usuário.
- **Criptografia:** A criptografia protege dados sensíveis através da transformação dos dados em uma forma ilegível, que só pode ser decifrada com uma chave de criptografia adequada, garantindo assim a confidencialidade e a integridade dos dados.
- **Gestão de Identidade e Acesso (IAM):** Os serviços de IAM ajudam a gerenciar identidades digitais de usuários e garantir que apenas usuários autorizados tenham acesso aos recursos apropriados, de acordo com suas funções e permissões.

## 5. Liste e defina resumidamente as categorias dos mecanismos de segurança.

- **Autenticação:** O mecanismo de autenticação verifica a identidade de um usuário ou dispositivo que está tentando acessar um sistema, rede ou recurso, garantindo que apenas usuários autorizados possam acessar esses recursos.
- **Autorização:** Este mecanismo determina quais recursos um usuário autenticado tem permissão para acessar e quais operações específicas ele pode realizar sobre esses recursos, com base em suas credenciais e nos controles de acesso definidos.
- **Criptografia:** A criptografia protege dados sensíveis transformando-os em uma forma ilegível que só pode ser decifrada por usuários autorizados que possuem a chave de criptografia correspondente, garantindo assim a confidencialidade e a integridade dos dados.
- **Integridade de Dados:** Mecanismos de integridade de dados garantem que os dados permaneçam completos, precisos e não corrompidos durante o armazenamento, transmissão e processamento, protegendo contra modificações não autorizadas ou corrupção de dados.
- **Controle de Acesso:** Esse mecanismo limita o acesso a recursos de sistema, redes e dados apenas a usuários autorizados, utilizando políticas de controle de acesso, como listas de controle de acesso (ACLs) e papéis de usuário.
- **Auditoria e Monitoramento:** Mecanismos de auditoria e monitoramento registram e acompanham atividades de usuários e sistemas em um ambiente de TI, permitindo a detecção de comportamentos suspeitos ou violações de segurança e facilitando a investigação forense.
- **Prevenção de Intrusões:** Este mecanismo identifica e bloqueia atividades maliciosas, como ataques de negação de serviço (DoS), exploração de vulnerabilidades e tentativas de acesso não autorizado, protegendo assim os sistemas contra comprometimentos de segurança.

## 6. Requisitos de Confidencialidade, Integridade e Disponibilidade para um Sistema ATM

### Confidencialidade:
- **Exemplo:** Os dados do usuário, como informações da conta e PIN (Personal Identification Number), devem ser mantidos em sigilo para evitar acesso não autorizado por terceiros.
- **Importância:** Extremamente alta. A divulgação de informações confidenciais pode levar a fraudes financeiras e comprometer a segurança financeira dos clientes.

### Integridade:
- **Exemplo:** As transações realizadas pelo usuário, como saques ou depósitos, devem ser registradas com precisão e não devem ser alteradas após a conclusão.
- **Importância:** Muito alta. A integridade dos dados é essencial para garantir que as transações sejam processadas corretamente e que não ocorram erros ou manipulações que possam afetar o saldo da conta ou causar perdas financeiras.

### Disponibilidade:
- **Exemplo:** O sistema ATM deve estar operacional e acessível aos usuários durante o horário de funcionamento esperado, sem interrupções significativas.
- **Importância:** Alta. A disponibilidade do ATM é crucial para garantir que os clientes possam acessar seus fundos quando necessário, evitando inconvenientes e garantindo a confiança no serviço prestado.

Cada um desses requisitos desempenha um papel crítico na segurança e na funcionalidade do sistema ATM. A falta de qualquer um desses requisitos pode resultar em consequências graves para os usuários, como perda financeira, exposição a fraudes e insatisfação com o serviço. Portanto, é essencial que o sistema ATM seja projetado e operado com medidas adequadas para garantir a confidencialidade, integridade e disponibilidade dos dados e dos serviços oferecidos.

## 7.
### a) Serviços de Segurança e Tipos de Ataques

|                                     | Ataque de Negação de Serviço | Interceptação de Dados | Modificação de Dados | Ataque de Força Bruta |
|-------------------------------------|------------------------------|------------------------|----------------------|-----------------------|
| Autenticação de Entidade Pareada    | Sim                          | Sim                    | Não                  | Não                   |
| Autenticação da Origem de Dados     | Sim                          | Sim                    | Não                  | Não                   |
| Controle de Acesso                  | Não                          | Não                    | Sim                  | Não                   |
| Confidencialidade                   | Sim                          | Não                    | Não                  | Não                   |
| Confidencialidade do Fluxo de Tráfego| Sim                          | Não                    | Não                  | Não                   |
| Integridade de Dados                | Sim                          | Não                    | Não                  | Sim                   |
| Responsabilização                   | Não                          | Sim                    | Não                  | Não                   |
| Disponibilidade                     | Não                          | Não                    | Sim                  | Não                   |

Nesta matriz:
- "Sim" indica que o serviço de segurança é eficaz contra o tipo de ataque listado.
- "Não" indica que o serviço de segurança não é eficaz contra o tipo de ataque listado.

### b) Mecanismos de Segurança e Tipos de Ataques

|                                    | Ataque de Negação de Serviço | Interceptação de Dados | Modificação de Dados | Ataque de Força Bruta |
|------------------------------------|------------------------------|------------------------|----------------------|-----------------------|
| Codificação                        | Sim                          | Sim                    | Não                  | Não                   |
| Assinatura Digital                 | Sim                          | Sim                    | Não                  | Não                   |
| Controle de Acesso                 | Não                          | Não                    | Sim                  | Não                   |
| Integridade de Dados               | Sim                          | Não                    | Não                  | Sim                   |
| Troca de Autenticação              | Sim                          | Não                    | Não                  | Não                   |
| Preenchimento de Tráfego           | Não                          | Não                    | Não                  | Sim                   |
| Controle de Roteamento             | Não                          | Não                    | Não                  | Sim                   |
| Notarização                        | Não                          | Não                    | Sim                  | Não                   |

Nesta matriz:
- "Sim" indica que o mecanismo de segurança é eficaz contra o tipo de ataque listado.
- "Não" indica que o mecanismo de segurança não é eficaz contra o tipo de ataque listado.
