# Regras Funcionais Iniciais

> Este documento registra decisões confirmadas na entrevista inicial. Regras
> detalhadas e casos de borda serão refinados antes da implementação.

## Perfis

| Perfil | Responsabilidades |
|---|---|
| Administrador | Acesso completo; gerencia usuários, perfis e configurações |
| Bibliotecário | Gerencia livros, exemplares, reservas, retiradas e devoluções |
| Leitor | Consulta o catálogo e gerencia suas próprias reservas e empréstimos |

O cadastro de leitor é público e fica ativo imediatamente.

## Catálogo

Um livro possui título, autores, editora, ano de lançamento, número de páginas,
categoria, localização na biblioteca e status. Um livro pode possuir um ou mais
exemplares físicos.

Cada exemplar possui:

- código único;
- localização física;
- status.

Status inicialmente previstos: `DISPONIVEL`, `RESERVADO`, `EMPRESTADO`,
`MANUTENCAO` e `INATIVO`.

## Reservas

- O leitor informa um período de início e fim.
- O período deve ser futuro e válido.
- O mesmo exemplar não pode ter reservas sobrepostas para pessoas diferentes.
- Uma reserva começa associada a um exemplar físico.
- O exemplar deve estar disponível para o período solicitado.
- Uma reserva não retirada até 24 horas após seu início é cancelada e libera o
  exemplar.

## Empréstimos

O fluxo previsto é:

1. `RESERVADO`: reserva criada para um período.
2. `EMPRESTADO`: bibliotecário registra a retirada.
3. `RENOVADO`: empréstimo renovado dentro dos limites permitidos.
4. `DEVOLVIDO`: bibliotecário registra a devolução.

Uma devolução após o prazo fica marcada como atrasada e bloqueia novas reservas do
leitor até a regularização. Não haverá cálculo de multa financeira na primeira
versão.

## Renovações

- O limite inicial é 3 renovações.
- O administrador pode alterar o limite no painel administrativo.
- A renovação não é permitida se houver reserva futura de outra pessoa para o
  exemplar.
- A renovação deve preservar a consistência dos períodos e da disponibilidade.

## Autorização

- Operações administrativas devem exigir o perfil `ADMINISTRADOR`.
- Operações de catálogo e circulação devem exigir `BIBLIOTECARIO` ou `ADMINISTRADOR`.
- Operações de consulta e gestão própria devem exigir `LEITOR` autenticado.
- Um leitor não pode acessar reservas, empréstimos ou dados privados de outro leitor.

## Cenários mínimos de teste

1. Leitor autenticado reserva exemplar disponível.
2. Segundo leitor tenta reservar o mesmo exemplar em período sobreposto.
3. Retirada transforma reserva em empréstimo.
4. Devolução libera o exemplar.
5. Renovação é bloqueada por reserva futura de outro leitor.
6. Reserva não retirada após 24 horas é cancelada.
7. Usuário sem perfil adequado recebe resposta de acesso negado.
