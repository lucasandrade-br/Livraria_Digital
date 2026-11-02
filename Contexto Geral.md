A ideia desse diretório é criar um sistema de conclusão acadêmica com base na solicitação do professor. Devemos nos basear em um projeto construído por ele (enviado via github) e desenvolvermos o nosso software. A solicitação detalhada da professor vem a seguir:

-> Objetivo:
Desenvolver um sistema web completo com base no projeto Ingresso (link do github em anexo), aplicando os conceitos de integração entre frontend e backend, persistência de dados, autenticação e regras de negócio.

-> Projeto de referência:
https://github.com/ferreiralisson/ingresso

*A arquitetura e as tecnologias do projeto do github servirão como referência, enquanto as entidades, funcionalidades e regras deverão ser adaptadas ao contexto indicado.

-> Contexto de software:
1. Controle de livros de uma biblioteca
2. Rota base para a API /livros 

-> Requisitos:
Manter o backend em Java com Spring Boot e o frontend em Angular, com comunicação por API REST, persistência com JPA e organização em camadas: controller, service e repository.
1. Implementar cadastro, login com JWT e controle de acesso por perfil. Cada usuário deverá acessar apenas os dados e as operações para os quais possui autorização.Adaptar as entidades, os relacionamentos, os endpoints e as telas ao tema atribuído. Implementar cadastro, consulta, atualização e exclusão ou inativação dos principais registros, conforme as regras do negócio.
2. Desenvolver um fluxo principal completo, equivalente ao fluxo de pedidos do projeto-base. Conforme o tema, esse fluxo poderá representar uma compra, reserva, agendamento, empréstimo ou solicitação, com controle de disponibilidade, acompanhamento de status e histórico do usuário.
3. Implementar as validações e regras específicas do tema, como impedir duplicidades, limitar quantidades, verificar disponibilidade e estabelecer condições de cancelamento. Quando houver pagamento ou reembolso, utilizar simulação, conforme o projeto-base.
4. Integrar as telas à API, apresentando mensagens de sucesso, validação e erro. Adaptar os testes às principais regras implementadas e aos cenários de acesso não autorizado.
5. 

6. A adaptação deverá ir além da troca de nomes, cores e imagens: o funcionamento do sistema precisa fazer sentido para o tema escolhido. Recursos específicos de ingressos, como QR Code e validação de entrada, deverão ser adaptados quando houver equivalente no novo domínio; caso contrário, justificar sua não utilização no README.