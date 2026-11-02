# Biblioteca Digital — Diretrizes do Projeto

## Objetivo

Este repositório contém o sistema acadêmico **Biblioteca Digital**, uma aplicação web
para catálogo, reservas e empréstimos de livros. O objetivo é demonstrar a integração
entre frontend e backend, persistência, autenticação, autorização, regras de negócio,
testes e organização arquitetural.

## Estrutura

- `Backend/`: API REST em Java com Spring Boot, organizada como monólito modular.
- `Frontend/`: aplicação Angular responsável pela interface e integração com a API.
- `Material de Documentação/`: documentação central, decisões arquiteturais e regras
  compartilhadas do sistema.
- Cada módulo deverá manter seu `README.md` dentro do próprio diretório, contendo
  responsabilidades, dependências, contratos, integrações, arquitetura interna e
  instruções de teste.
- Documentação específica de um módulo deve permanecer dentro daquele módulo.

## Princípios de desenvolvimento

- Seguir SDD: especificar e documentar antes de implementar; manter a documentação
  atualizada após cada mudança relevante.
- Aplicar SOLID, DRY, KISS, coesão alta e baixo acoplamento.
- Manter responsabilidades separadas; não misturar domínio, persistência,
  apresentação, configuração e integração na mesma classe ou diretório.
- Preferir nomes claros e consistentes. Identificadores de código devem usar inglês;
  documentação funcional e técnica deve usar português do Brasil.
- Não duplicar regras de negócio entre controllers, componentes e serviços.
- Validar entradas e retornar erros explícitos, consistentes e úteis para a interface.
- Alterações de comportamento devem atualizar especificações, testes e READMEs
  relacionados.

## Arquitetura técnica

- Backend: Java 21, Spring Boot 3.x, API REST, Spring Data JPA e PostgreSQL.
- Frontend: Angular em versão LTS.
- Autenticação: JWT.
- Autorização: perfis `ADMINISTRADOR`, `BIBLIOTECARIO` e `LEITOR`.
- O sistema deve permanecer como monólito modular; não criar microsserviços.
- A rota base da API para o domínio de livros é `/livros`.

## Regras funcionais já confirmadas

- Livros possuem exemplares físicos identificados por código único.
- Um exemplar não pode ser reservado por duas pessoas em períodos sobrepostos.
- O leitor pode consultar o catálogo e reservar exemplares disponíveis.
- O fluxo principal é: reservar, retirar, renovar quando permitido e devolver.
- A retirada deve ocorrer até 24 horas após o início da reserva; depois disso, a
  reserva é cancelada e o exemplar é liberado.
- O limite inicial de renovações é 3 e deve ser configurável pelo administrador.
- Uma renovação não é permitida quando existe reserva futura de outra pessoa.
- Devoluções atrasadas bloqueiam novas reservas até a regularização, sem multa
  financeira na primeira versão.
- O cadastro de leitor é público e fica ativo imediatamente.
- O administrador gerencia usuários, perfis e configurações.
- O bibliotecário gerencia catálogo, exemplares e circulação, mas não usuários.
- O leitor consulta livros e gerencia suas próprias reservas/empréstimos.

## Qualidade e validação

- Criar testes para o fluxo de sucesso e para bloqueios de regras de negócio.
- Cobrir autorização, validação de dados, conflitos de reserva e transições de status.
- Antes de considerar uma tarefa concluída, executar a menor validação adequada e
  atualizar a documentação correspondente.
- Não adicionar dependências sem registrar sua finalidade e impacto no README do
  módulo afetado.

## Documentação de referência

- [Visão geral do sistema](Material%20de%20Documentação/README.md)
- [Regras funcionais iniciais](Material%20de%20Documentação/Regras%20Funcionais%20Iniciais.md)
- [Contexto fornecido pelo professor](Contexto%20Geral.md)