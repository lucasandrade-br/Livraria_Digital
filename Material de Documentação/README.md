# Biblioteca Digital — Documentação Central

## Finalidade

Este diretório concentra as decisões e especificações que atravessam o backend e o
frontend. A documentação específica de cada módulo deve permanecer no diretório do
próprio módulo.

## Produto

O **Biblioteca Digital** é um sistema web para gerenciamento de livros de uma
biblioteca. Usuários autenticados podem consultar o catálogo e reservar exemplares
físicos. Bibliotecários controlam catálogo e circulação; administradores controlam
usuários, perfis e configurações.

## Objetivo acadêmico

A entrega deve demonstrar:

- fluxo principal funcionando;
- cenário de sucesso;
- cenário bloqueado por regra de negócio;
- integração frontend/backend;
- persistência de dados;
- autenticação e autorização;
- validações e testes;
- organização do código e domínio da solução pelos cinco integrantes.

## Escopo confirmado da primeira versão

- Cadastro e login com JWT.
- Perfis administrador, bibliotecário e leitor.
- Catálogo com livros e exemplares físicos.
- Consulta e filtros de livros.
- Reserva com período definido e prevenção de sobreposição.
- Retirada, devolução, renovação e cancelamento por não retirada.
- Controle de atrasos sem multa financeira.
- Painel administrativo e gestão de livros.
- Telas de login/cadastro, catálogo, detalhes/reserva, minhas reservas,
  painel administrativo e gestão de livros.

## Stack inicial

- Backend: Java 21, Spring Boot 3.x, Spring Data JPA e PostgreSQL.
- Frontend: Angular em versão LTS.
- Comunicação: API REST.
- Organização: monólito modular com separação clara de responsabilidades.

## Cenários de apresentação

### Sucesso

Um leitor autenticado consulta um exemplar disponível, cria uma reserva, retira o
livro e o bibliotecário registra a devolução.

### Bloqueio

Um segundo leitor tenta reservar o mesmo exemplar em período sobreposto. A API
recusa a operação, informa a indisponibilidade e não cria uma reserva.

## Documentos

- [Regras funcionais iniciais](Regras%20Funcionais%20Iniciais.md)
- [Roteiro de idealização e documentação](Roteiro%20de%20Idealização%20e%20Documentação.md)
- [Contexto original do projeto](../Contexto%20Geral.md)

## Documentos planejados

Os próximos artefatos serão produzidos após o levantamento arquitetural:

- visão de módulos e responsabilidades;
- modelo de domínio e relacionamentos;
- contratos da API;
- matriz de permissões;
- arquitetura frontend;
- estratégia de testes;
- decisões arquiteturais (ADR);
- plano de entrega até 16/11.
