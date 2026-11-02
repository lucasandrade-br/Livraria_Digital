# Roteiro de Idealização e Documentação

## 1. Objetivo

Este documento define as rodadas de entrevistas, decisões e registros que devem
ocorrer antes e durante o desenvolvimento da **Biblioteca Digital**. O objetivo é
garantir que o sistema seja compreendido, especificado, implementado e validado de
forma rastreável, sem decisões importantes implícitas.

O roteiro abrange:

- visão do produto e objetivos acadêmicos;
- usuários, permissões e jornadas;
- regras de negócio e casos de exceção;
- modelo de domínio e dados;
- arquitetura do monólito modular;
- organização de diretórios e arquivos;
- contratos de frontend e backend;
- segurança, validação e tratamento de erros;
- testes, qualidade e apresentação;
- execução, entrega e manutenção da documentação.

## 2. Princípios das rodadas

1. Cada rodada deve resultar em decisões registradas.
2. Toda decisão deve indicar se é obrigatória, recomendada ou pendente.
3. Decisões conflitantes devem ser resolvidas antes da implementação da área
   afetada.
4. Uma mudança de comportamento exige atualização da especificação, dos testes e
   da documentação do módulo.
5. A documentação central registra decisões compartilhadas; a documentação
   específica permanece no módulo que a utiliza.
6. Nenhuma rodada deve criar código de produção antes de seu critério de saída ser
   atendido.
7. As decisões devem priorizar um MVP demonstrável até 16/11, sem comprometer a
   possibilidade de evolução.

## 3. Artefatos e estados

Cada assunto deve passar por estes estados:

- **Em descoberta**: perguntas ainda estão sendo debatidas.
- **Proposto**: existe uma alternativa recomendada, mas falta confirmação.
- **Confirmado**: decisão aprovada e registrada.
- **Implementado**: comportamento aplicado ao código.
- **Validado**: testes ou evidências confirmam o comportamento.
- **Obsoleto**: decisão substituída, mantendo histórico da alteração.

## 4. Rodadas de idealização

### Rodada 01 — Visão, objetivos e restrições

**Debater**

- problema que o sistema resolve;
- objetivo acadêmico e critérios de avaliação;
- público-alvo;
- escopo da primeira entrega;
- prazo, equipe e divisão inicial de responsabilidades;
- funcionalidades fora do escopo;
- restrições técnicas, acadêmicas e operacionais;
- critérios de sucesso do produto.

**Documentar**

- visão geral do produto;
- objetivos acadêmicos;
- escopo e fora de escopo;
- premissas, restrições e riscos iniciais;
- glossário inicial.

**Critério de saída**

O propósito, o MVP, as restrições e os critérios de sucesso estão confirmados.

### Rodada 02 — Personas, perfis e autorização

**Debater**

- personas e necessidades;
- cadastro, ativação, recuperação de acesso e encerramento de conta;
- perfis e permissões;
- operações permitidas e proibidas por perfil;
- dados públicos, privados e administrativos;
- troca ou acúmulo de perfis;
- comportamento para usuário não autenticado.

**Documentar**

- personas;
- matriz de permissões;
- política de autenticação e autorização;
- jornadas de acesso;
- decisões sobre proteção de dados.

**Critério de saída**

Cada operação do MVP possui um perfil autorizado, uma regra de propriedade e um
comportamento para acesso negado.

### Rodada 03 — Jornadas e fluxos principais

**Debater**

- jornada do leitor;
- jornada do bibliotecário;
- jornada do administrador;
- fluxo feliz ponta a ponta;
- estados e transições;
- notificações e mensagens visíveis;
- pontos de abandono, cancelamento e retomada.

**Documentar**

- jornadas dos usuários;
- fluxos funcionais;
- diagramas de sequência ou atividades;
- critérios de aceite por fluxo.

**Critério de saída**

Os fluxos de apresentação e todos os fluxos essenciais têm início, fim, atores,
pré-condições, pós-condições e erros definidos.

### Rodada 04 — Regras de negócio e exceções

**Debater**

- disponibilidade;
- conflitos de reserva;
- prazos;
- retirada, devolução e renovação;
- atrasos e bloqueios;
- cancelamentos;
- concorrência entre operações;
- limites configuráveis;
- comportamento em datas, horários e feriados;
- auditoria de alterações.

**Documentar**

- regras funcionais numeradas;
- tabela de estados;
- invariantes do domínio;
- casos de borda;
- mensagens e códigos de erro de negócio;
- exemplos de sucesso e bloqueio.

**Critério de saída**

Cada regra possui condição, ação, exceção, resultado esperado e cenário de teste.

### Rodada 05 — Vocabulário e modelo de domínio

**Debater**

- significado de livro, exemplar, reserva e empréstimo;
- entidades, objetos de valor e agregados;
- identificadores;
- relacionamentos e cardinalidades;
- ciclo de vida de cada entidade;
- histórico e auditoria;
- campos obrigatórios, opcionais e derivados;
- regras que pertencem ao domínio.

**Documentar**

- glossário oficial;
- modelo conceitual;
- diagrama de entidades e relacionamentos;
- dicionário de dados;
- máquina de estados das entidades.

**Critério de saída**

Não existem termos ambíguos, entidades sem responsabilidade ou regras sem
proprietário no domínio.

### Rodada 06 — Persistência e banco de dados

**Debater**

- PostgreSQL e ambientes;
- tabelas, chaves e índices;
- unicidade;
- integridade referencial;
- transações;
- estratégia de migração;
- dados iniciais para demonstração;
- paginação e filtros;
- exclusão física, inativação e retenção histórica.

**Documentar**

- modelo lógico do banco;
- convenções de nomenclatura;
- estratégia de migrações;
- índices e justificativas;
- seed de demonstração;
- política de backup para ambientes relevantes.

**Critério de saída**

O modelo suporta as regras confirmadas e os cenários concorrentes sem depender de
validações apenas no frontend.

### Rodada 07 — Arquitetura geral e modularização

**Debater**

- limites do monólito modular;
- módulos e responsabilidades;
- dependências permitidas entre módulos;
- camadas;
- fronteiras entre domínio, aplicação, infraestrutura e apresentação;
- eventos internos, se necessários;
- configuração compartilhada;
- decisões que não devem virar microsserviços.

**Documentar**

- visão arquitetural;
- mapa de módulos;
- regras de dependência;
- diagramas de componentes;
- decisões arquiteturais (ADRs);
- responsabilidades e interfaces de cada módulo.

**Critério de saída**

Cada responsabilidade possui um único módulo proprietário e as dependências
permitidas estão explícitas.

### Rodada 08 — Organização de diretórios e arquivos

**Debater**

- estrutura raiz;
- estrutura de `Backend/`;
- estrutura de `Frontend/`;
- localização de testes;
- localização de configurações;
- separação de domínio, persistência, API e apresentação;
- convenções de nomes;
- arquivos proibidos ou com responsabilidade misturada;
- necessidade e escopo de `AGENTS.md` internos;
- README obrigatório por módulo.

**Documentar**

- árvore de diretórios aprovada;
- convenções de arquivos;
- responsabilidade de cada pasta;
- regras para criação de novos módulos;
- regra de co-localização de testes e documentação;
- `AGENTS.md` da raiz e, se necessário, dos módulos.

**Critério de saída**

Uma pessoa consegue decidir onde criar qualquer novo arquivo sem misturar
responsabilidades.

### Rodada 09 — Backend, API e contratos

**Debater**

- endpoints;
- verbos e códigos HTTP;
- formato de requisição e resposta;
- paginação, filtros e ordenação;
- autenticação JWT;
- versionamento;
- validação;
- tratamento global de erros;
- idempotência;
- concorrência;
- documentação OpenAPI;
- rota base `/livros`.

**Documentar**

- catálogo de endpoints;
- contratos JSON;
- matriz de autenticação;
- códigos de erro;
- padrões de resposta;
- exemplos de chamadas;
- contrato OpenAPI, quando criado.

**Critério de saída**

Frontend e backend conseguem desenvolver contra contratos estáveis e todos os
erros esperados possuem resposta consistente.

### Rodada 10 — Frontend, navegação e experiência

**Debater**

- telas e rotas;
- layout e identidade visual;
- componentes reutilizáveis;
- formulários e validações;
- estados de carregamento, vazio, sucesso e erro;
- guardas de rota;
- mensagens para o usuário;
- acessibilidade;
- responsividade;
- gerenciamento de estado;
- interceptação de autenticação.

**Documentar**

- mapa de telas;
- fluxos de navegação;
- responsabilidades dos componentes;
- contratos dos serviços frontend;
- padrões visuais e de interação;
- critérios de acessibilidade.

**Critério de saída**

Cada requisito do MVP possui tela, estado visual, ação do usuário e integração
definidos.

### Rodada 11 — Segurança e proteção de dados

**Debater**

- armazenamento seguro de senhas;
- emissão, validade e revogação de JWT;
- autorização no backend;
- validação e sanitização;
- exposição de dados;
- CORS;
- proteção contra abuso;
- logs sem dados sensíveis;
- segredos e variáveis de ambiente;
- permissões administrativas.

**Documentar**

- modelo de ameaça proporcional ao MVP;
- política de autenticação;
- política de autorização;
- classificação de dados;
- gestão de segredos;
- requisitos de segurança e cenários de teste.

**Critério de saída**

As regras de acesso são aplicadas no backend, os dados sensíveis não são expostos
e os cenários de acesso indevido estão testados.

### Rodada 12 — Testes e qualidade

**Debater**

- testes unitários;
- testes de integração;
- testes de API;
- testes frontend;
- testes de autorização;
- testes de banco;
- cenários de concorrência;
- dados de teste;
- cobertura mínima relevante;
- lint, formatação e análise estática.

**Documentar**

- estratégia de testes;
- matriz requisito-cenário;
- convenções de testes;
- comandos oficiais;
- critérios de aprovação;
- evidências dos cenários da apresentação.

**Critério de saída**

Todo requisito crítico possui pelo menos um teste positivo e um teste de bloqueio
ou erro, quando aplicável.

### Rodada 13 — Execução local, ambientes e operação

**Debater**

- instalação;
- Java, Node.js, Angular CLI e PostgreSQL;
- Docker Compose;
- variáveis de ambiente;
- migrações;
- usuários de demonstração;
- execução backend/frontend;
- logs;
- diagnóstico de falhas;
- preparação da apresentação.

**Documentar**

- README de execução;
- requisitos de ambiente;
- comandos de desenvolvimento e teste;
- configuração de variáveis;
- procedimento de carga inicial;
- solução de problemas comuns.

**Critério de saída**

Uma pessoa nova consegue executar o sistema e reproduzir os cenários da
apresentação seguindo apenas a documentação.

### Rodada 14 — Divisão da equipe e governança

**Debater**

- responsabilidades dos cinco integrantes;
- fronteiras de alteração;
- fluxo de revisão;
- convenção de branches e commits;
- definição de pronto;
- comunicação de mudanças;
- prevenção de conflitos;
- preparação individual para apresentação.

**Documentar**

- matriz de responsabilidades;
- fluxo de trabalho;
- checklist de revisão;
- definição de pronto;
- roteiro de demonstração por integrante.

**Critério de saída**

Cada integrante possui uma área compreensível e consegue explicar as decisões e o
funcionamento da solução.

### Rodada 15 — Plano de implementação e priorização

**Debater**

- ordem de implementação;
- dependências entre tarefas;
- fatias verticais do MVP;
- riscos;
- funcionalidades opcionais;
- marcos até 16/11;
- pontos de validação;
- estratégia para não deixar integração para o final.

**Documentar**

- backlog priorizado;
- plano de implementação;
- dependências;
- marcos;
- riscos e mitigação;
- checklist de cada entrega.

**Critério de saída**

O MVP está dividido em tarefas executáveis, ordenadas por dependência e com
validação prevista.

### Rodada 16 — Validação final e preparação da apresentação

**Debater**

- fluxo completo em ambiente limpo;
- cenários de sucesso e bloqueio;
- evidências de testes;
- consistência da documentação;
- pendências aceitáveis;
- roteiro de apresentação;
- perguntas técnicas prováveis;
- plano de contingência.

**Documentar**

- relatório de validação;
- checklist de entrega;
- roteiro final;
- limitações conhecidas;
- decisões futuras;
- versão final da documentação.

**Critério de saída**

O sistema inicia, executa o fluxo principal, demonstra o bloqueio de negócio,
passa pelas validações definidas e possui documentação coerente com o código.

## 5. Ciclo contínuo após cada mudança

Para toda alteração relevante:

1. identificar a decisão ou requisito afetado;
2. atualizar a documentação antes ou junto da implementação;
3. atualizar contratos, testes e README do módulo, quando aplicável;
4. implementar a mudança no módulo responsável;
5. executar a menor validação adequada;
6. verificar impactos em outros módulos;
7. registrar a decisão e a evidência;
8. marcar como validada somente após os testes.

## 6. Documentação esperada por camada

### Raiz

- `AGENTS.md`;
- visão geral e regras compartilhadas;
- roteiro de idealização;
- decisões arquiteturais transversais;
- plano e critérios de entrega.

### Backend

- README de execução;
- README de arquitetura;
- README por módulo;
- contratos da API;
- persistência e migrações;
- testes e regras de negócio;
- `AGENTS.md` específico, se houver convenções diferentes da raiz.

### Frontend

- README de execução;
- README de arquitetura;
- README por módulo ou feature;
- mapa de telas e navegação;
- padrões de componentes;
- integração com a API;
- testes;
- `AGENTS.md` específico, se houver convenções diferentes da raiz.

## 7. Ordem recomendada a partir de agora

As rodadas 01 a 04 já foram iniciadas e possuem decisões preliminares. A próxima
atividade deve ser revisar e confirmar as lacunas dessas rodadas. Depois, seguir
para:

1. Rodada 05 — modelo de domínio;
2. Rodada 06 — persistência;
3. Rodada 07 — arquitetura e módulos;
4. Rodada 08 — diretórios, arquivos e `AGENTS.md` internos;
5. Rodadas 09 e 10 — contratos backend e frontend;
6. Rodadas 11 e 12 — segurança e testes;
7. Rodadas 13 a 16 — execução, equipe, implementação e entrega.

Nenhum módulo deve ser considerado pronto sem README, testes pertinentes,
documentação atualizada e validação registrada.
