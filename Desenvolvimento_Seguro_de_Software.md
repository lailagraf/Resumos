# Curso: Desenvolvimento Seguro de Software (Básico)

## Módulo 0 - Pilares de Segurança no Desenvolvimento do Software (Introdução)

### Definições

**Software:** é um conjunto de programas que permite aos usuários realize uma função bem definida ou uma tarefa específica. é composto por linguagem binária mas pode ser escrito com linguagens mais legíveis por humanos.

**Segurança da Informação:** Ato de proteger dados e informações.

**Segurança de sistemas da informação:** Ato de proteger os sistemas que mantêm e processam os dados.

**Dados:** Todas as informações processadas pelo software e, até mesmo, o próprio software.
  - *Dados Estruturados:* são aqueles organizados e representados como uma estrutura rígida, a qual foi previamente planejada para armazená-los.
  - *Dados não-estruturados:* Uma estrutura flexível e dinâmica ou sem estrutura.
  - *Dados semi-estruturados:* Apresentam uma representação heterogênea, possuem estrutura mas ela é flexível. Ex: JSON, RDF, OWL.

**Superfície de ataque:** número de maneiras possíveis ou "vetores de ataque", que um "agente de ameaça" pode usar para interagir com recursos da aplicação.
  - *Agente de Ameaça:* Alguém ou alguma coisa que manifesta ou representa uma ameaça.
  - *Ameaça:* Uma ameaça pode ser uma intenção expressa ou demonstrada de prejudicar um ativo ou fazer com que ele se torna indisponível.
  - *Vulnerabilidades:* Uma fraqueza de um ativo que poderia ser potencialmente explorado por uma ou  mais ameaças.  
  - *Vetores de ataque:* É uma maneira de os invasores entrarem em uma rede ou sistema. Ou seja, qual meio ele vai usar para atacar uma vulnerabilidade. (Phishing, Explorações de vulnerabilidade, Invasão de contas)
  - *Risco:* É a possibilidade de perda, dano ou destruição de um ativo como resultado da exploração de uma vulnerabilidade por uma ameaça.
  - *Ataque:* É qualquer tentativa de expor, alterar, desativar, destruir, roubar ou obter acesso não autorizado ou fazer uso não autorizado de um dispositivo ou informação.
  - *Incidente de segurança:* É um evento de segurança ou um conjunto deles, confirmado ou sob suspeita de impactar a disponibilidade. integridade ou a autenticidade.

**Arquitetura segura:** estrutura de design de sistema que é projetada para proteger contra ameaças cibernéticas, garantir a privacidade dos dados e prevenir violações de segurança.

**Ausência de Segurança:**
- *Vulnerabilidades em softwares:*
  - Codificação insegura:
    - Bibliotecas desatualizadas;
    - Códigos prontos de fontes desconhecidas;
    - "Agilidade" no desenvolvimento;
- Consideração apenas de cenários positivos;
- Descarte do uso por usuários maliciosos.

## Módulo 1 - Controles e Padrões de Segurança da Informação

### Tríade CID
> Modelo de segurança da informação que visa proteger a confidencialidade, integralidade e disponibilidade das informações em um sistema de tecnologia da informação.

**Pilares:**
- *Confidencialidade:* deve garantir a restrição de acesso à informações por pessoas não autorizadas.
- *Integridade:* deve garantir que a informação seja completa e exata, além de prevenir que usuários sem autorização façam modificações nelas.
- *Disponibilidade:* deve garantir que a informação esteja completa e exata, além de prevenir que os usuários sem autorização façam modificações nelas.
- *Disponibilidade:* deve garantir que a informação esteja acessível e utilizável sempre que necessário.
- *Autenticidade:* deve validar a autorização do usuário para acessar, transmitir e receber determinadas informações.
- *Irretratabilidade:* garante que uma pessoa ou entidade não possa negar a autoria da informação fornecida.


### Os 3 As da segurança
> Abordagem para segurança da informação que visa proteger as informações através de 3 princípios básicos.

- **Autenticação:** é uma referência ao procedimento que confirma a validade do usuário que realiza a requisição de um serviço.
- **Autorização:** é a concessão de uso para determinados tipos de serviço, dada a um usuário previamente autenticado com base na sua identidade, nos serviços que requisita e no estado atual do sistema. A autorização pode ser baseada em restrições que são definidas por um horário de permissão de acesso ou localização física do usuário, por exemplo.
- **Auditoria:** É uma referência à coleta da informação relacionada à utilização de recursos de rede pelos usuários. Esta informação pode ser utilizada para gerenciamento, planejamento, cobrança e etc. As informações que são tipicamente relacionados com este processo são a identidade do usuário, a natureza do serviço entregue, o momento em que o serviço se inicia e o momento do seu término.

### Gerenciamento de Risco
> Frente de trabalho específica cujo objetivo é identificar os possíveis riscos e reduzir os impactos negativos que eles podem causar, permitindo o tratamento, aceitando ou terceirizando seus efeitos, que por via de regra acarreta prejuízos financeiros, nas metas e resultados não atingidos, processos judiciais e desgastes com imagem e reputação da companhia.

### Avaliação de Risco
> Técnica utilizada para identificar, analisar e avaliar os riscos potenciais que uma organização ou sistema pode enfrentar.
1. Identificar os ativos da empresa
2. Identificar todas as vulnerabilidades
3. Identificar as ameaças
4. Identificar o impacto monetário

**Tipos de avaliação:**
1. *Avaliação passiva:* usada para identificar ameaças e vulnerabilidades em um sistema sem interromper ou afetar sua operação.
2. *Avaliação ativa:* feita por meio de testes, simulações e ataques controlados no ambiente, podendo afetá-lo.

### Cálculo de Risco:
> Avaliação que envolve a identificação de ameaças, vulnerabilidades e impactos potenciais em um sistema, como objetivo de determinar o nível de risco e implementar medidas adequadas de segurança.

- *Qualitativo:* Usa a intuição e experiência para atribuir valores a um determinado risco (baixo, médio, alto, crítico)
- *Quantitativo:* Depende de números e valores monetários como os valores do ativo, frequência da ameaça, gravidade de vulnerabilidade e impacto do possível incidente, ou seja, é o cálculo da estimativa de dados totais.

**Ações sobre riscos:** 
- *Evitar:* Parar a atividade que esta em risco ou escolher uma alternativa menos arriscada.
- *Transferir:* Passar o risco para terceiros, como uma seguradora.
- *Mitigar:* Eliminar ou minimizar o risco a um nível aceitável.
- *Aceitar:* Aceitar o nível atual de risco e os custos atuais à ele concretizando um incidente.

### Controle de segurança
>  Medidas de segurança aplicadas para modificar o risco a níveis aceitáveis.

Tipos:
- Preventivo;
- Detectivo;
- Corretivo.

### Princípio do Menor Privilégio
> Conceito de que um usuário deve ter acesso apenas ao que é absolutamente necessário para desempenhar suas responsabilidades e nada mais.

### Defesa em Profundidade/ Camadas: Controle Lógico
> Abordagem de gerenciamento de riscos de segurança que define várias camadas de controles em um ambiente de TI. As camadas múltiplas aumentam a pontuação geral de segurança do ambiente e reduzem a probabilidade de uma violação de segurança.

## Módulo 2 - Segurança no Desenvolvimento de Software (Introdução)

### Desafios no desenvolvimento seguro
- Os desenvolvedores se preocupam com a velocidade;
- Os desenvolvedores não são treinados em segurança;
- O treinamento de segurança é considerado um mal necessário;
- A segurança pode ser vista como um bloqueador;
- Desalinhamento de responsabilidades.

### AppSec
> Processo de localização, correção e prevenção de vulnerabilidades de segurança em nível de código.

### Security Champion
> Conceito no campo de segurança cibernética que se refere a um profissional de desenvolvimento de software que é designado para promover a segurança dentro da organização. Esses profissionais são geralmente membros da equipe de desenvolvimento que são selecionados e treinados para serem especialistas em segurança cibernética.

### Ciclo de Vida de Desenvolvimento do Software (SDLC)
> Processo que descreve as etapas envolvidas no desenvolvimento de software, desde a concepção até a retirada do software. O SLDC é uma estrutura para gerenciar projetos de desenvolvimento de software e garantir que o software seja desenvolvido com eficiência, qualidade e segurança.

**Metodologias:**
- *Waterfall:* Segue uma abordagem sequencial, com cada fase do processo de desenvolvimento concluída antes de passar para a próxima fase. As fases incluem análise de requisitos, design, implementação, testes e manutenção.
- *Agile:* Este modelo é baseado em colaboração, feedback contínuo e entregas iterativas. Os desenvolvedores trabalham em sprints curtos, com cada sprint entregando um produto funcional.
- *DevOps:* Este modelo enfatiza a colaboração entre desenvolvimento de software e operações de TI, a automação de processos e a entrega contínua.
- *Lean:* Este modelo se concentra na eliminação de desperdícios e na entrega de valor ao cliente o mais rapidamente possível.

### Ciclo de Vida de Desenvolvimento Seguro de Software (SSDLC)
> Modelo de SDLC que se concentra especificamente na segurança do software durante o processo de desenvolvimento. É uma abordagem proativa para a segurança, em que a segurança é incorporada no ciclo de vida do software desde o início do projeto.

## Módulo 3 - Testes de Segurança

### SAST (Código)
> "Static application security testing". Ferramentas utilizadas para análise de vulnerabilidade realizando a interpretação de uma linguagem utilizada no desenvolvimento e verificando possíveis brechas deixadas pra trás pelos desenvolvedores.

### DAST (Fluxo de dados)
> "Dynamic application security testing". Ferramentas utilizadas para análise de vulnerabilidade realizando a interpretação e emulação do fluxo de dados da aplicação em ambientes que se assemelham ao de produção e verificando possíveis brechas deixadas pra trás pelos desenvolvedores.

**SAST**|**DAST**
:----:|:-----:
Metodologia White box| Metodologia Black Box 
Requer código fonte| Requer aplicação em execução
Encontra vulnerabilidades no início do SDCL|Encontra vulnerabilidades no final do SDCL 
Mais barato para corrigir vulnerabilidades| Mais caro para corrigir vulnerabilidades
Não descobre problemas relacionados ao tempo de execução e ambiente| Descobre problemas relacionados ao tempo de execução e ambiente
Normalmente suporta todos os tipos de software| Normalmente verifica apenas aplicações web e serviços da web

**White Box:** O testador tem acesso à estrutura, design e implementação subjacentes. A aplicação é testada de dentro pra fora.

**Black Box:** O testador não possui conhecimento das tecnologias ou estruturas nas quais a aplicação é desenvolvida. É testada de fora pra dentro. 

### SCA
> "Software Composition Analysis". Prática de desenvolvimento que utiliza ferramentas de teste de segurança para gerenciamento do uso de código aberto. Execução de varreduras automáticas.

### Teste Unitários/ de Integração

**Teste unitário:** Realizado na menor parte testável da aplicação, ou seja, testes de funções simples.

**Teste de integração:** Teste executado em diferentes módulos do sistema, testando a integração de uma determinada funcionalidade.

### Code Review
> Revisão de código de uma determinada aplicação, normalmente feita a cada commit.

## Módulo 4 - OWASP Top 10:2021
> Riscos de segurança mais críticos em aplicações WEB.

- **Broken Access Control:** Restrições erradas para usuários autenticados;
- **Cryptographic Failures:** Dados não criptografados ou incorretamente criptografados;
- **Injection:** Falhas de injeção SQL, NoSQL, OS e LDAP. Dados não confiáveis são enviados para um interpretador como parte de um comandou ou consulta enganando o interpretador.
- **Insecure Design:** Riscos relacionados a falhas de design e arquitetura.
- **Security Misconfiguration:** Configuração incorreta de segurança.
- **Vulnerable and Outdated Components:** Componentes com vulnerabilidades, sem suporte ou desatualizados com os mesmos privilégios que a aplicação.
- **Identification and Authentication Failures:** Autenticação e gerenciamento de sessão implementados incorretamente, permitindo que invasores comprometam senhas, chaves ou tokens de sessão ou outras falhas.
- **Software and Data Integrity Failures:** Falhas de integridade relacionadas a atualizações sem verificação, dependência de plug-ins, bibliotecas ou módulos de fontes não confiáveis, pipeline de CI/CD inseguro, entre outros.
- **Security Logging and Monitoring Failures:** Registro de monitoramento insuficientes, adicionados a  integração ausente ou ineficaz com a resposta a incidentes.
- **Server-Side Request Forgery (SSRF):** Ataques que exploram relações de confiança para escalar um ataque do aplicativo vulnerável e executar ações não autorizadas contra o próprio servidor ou contra outros sistemas back-end.

## Módulo 5 - ASVS/ CWE

### OWASP ASVS
> Padrão desenvolvido pela OWASP que contempla uma lista de requisitos e controles de segurança de aplicações a fim de garantir que os controles tenham sido implementados durante o ciclo de desenvolvimento. Parte de uma estratégia de gestão de segurança de aplicações.

**Níveis de requisitos:**
- Aplicação não transacional: Nível mais básico que toda aplicação não-transacional deveria utilizar, como sites e blogs. Pode ser validado por meio de um pentest.
- Aplicação transacional: Recomendado para aplicações e sistemas que contém dados pessoais e é o nível recomendado para a maior parte das aplicações.
- Aplicações críticas: Recomendado para aplicações críticas e transacionais, que contém dados pessoais sensíveis, como registros médicos, dados financeiros ou qualquer outra aplicação que requeira um alto nível de confiabilidade.

### CWE
> "Common Weakness Enumeration". Lista desenvolvida pela comunidade de tipos comuns de fraqueza de software que têm ramificações de segurança. A lista CWE e a taxonomia de classificação associada servem como uma linguagem que pode ser usada para identificar e descrever essas fraquezas em termos de CWEs. Seu objetivo é interromper vulnerabilidades na fonte, educando os profissionais de desenvolvimento sobre como eliminar os erros mais comuns antes que os produtos sejam entregues.

## Módulo 6 - Modelagem de Ameaças

**Modelagem de ameaças** é um processo onde ameaças potenciais, vulnerabilidades ou a ausência de salvaguardas podem ser identificados e enumeradas. Seu objetivo é fornecer aos defensores uma análise de quais controles ou desas precisam ser incluídos, o provável perfil do invasor, os vetores de ataque mais esperados e os ativos mais desejados por um invasor.

**STRIDE:**
> Metodologia de modelagem de ameaças.

- **S**poofing: Falsificação, fingir ser outra pessoa;
- **T**ampering: Adulteração, alterar dados sem autorização;
- **R**epudiation: Repúdio, não reinvindicar a responsabilidade por uma ação executada;
- **I**nformation Disclouse: Divulgação de informações confidenciais, ver dados sem permissão;
- **D**enial of service: Negação de serviço, sobrecarregar o sistema;
- **E**levation of privilege: Elevação de privilégio, ter permissões que não se deveria ter. 
