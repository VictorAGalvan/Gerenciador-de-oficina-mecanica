# Gerenciador de Oficina Mecânica

## Descrição e escopo

Este mini-sistema tem como objetivo melhorar o fluxo de trabalho de uma oficina mecânica. A ideia surgiu de uma situação que observei em São Jorge, minha cidade, onde as ordens de serviço são feitas em folhas de papel e o estoque é conferido olhando a prateleira.

O sistema reúne em um só lugar o cadastro de clientes, veículos e peças, o controle de estoque, as ordens de serviço com orçamento e um calendário de atendimentos.

### Quem usa

O mecânico é o usuário principal: cadastra, controla o estoque, abre as ordens e organiza a agenda. O cliente recebe as notificações no WhatsApp, como o orçamento, o andamento da ordem e as cobranças. O sistema é pensado para oficinas de pequeno porte, e cada oficina usa sua própria instância, com banco de dados separado.

### O que o sistema faz

- Cadastra clientes, modelos de veículo e os veículos de cada cliente.
- Cadastra peças, controla as entradas e saídas do estoque avisa quando uma peça chega ao estoque mínimo e mostra em quais modelos cada peça serve.
- Abre ordens de serviço com orçamento, dá baixa nas peças usadas e registra a encomenda das que faltam.
- Envia o orçamento ao cliente, que aprova ou recusa por mensagem no WhatsApp. Se a mensagem falhar ou a resposta for inválida, o mecânico registra a decisão manualmente.
- Agenda atendimentos em um calendário.
- Registra a cobrança, quando o mecânico decide cobrar pelo sistema, e a confirmação do pagamento.
- Gera relatórios de clientes, veículos, estoque e ordens de serviço.

### O que fica de fora

O sistema não faz pagamentos: o cliente paga fora e o mecânico só registra. Por enquanto existe só um acesso, o da oficina. A ideia é atender a maioria das necessidades comuns da oficina. O que for fora do comum, o mecânico resolve do jeito que achar melhor.

## Principais pontos

### 1. Rapidez na utilização

O sistema deve ser rápido e simples de usar. Cada operação precisa ter poucos passos, porque uma curva de aprendizagem alta dificulta a adoção.

### 2. Poucas informações por tela

Cada tela mostra só o que é necessário para a tarefa do momento. Assim fica mais fácil achar o que se procura, sem distrações.

### 3. Compatibilidade entre peças e veículos

Cada peça é ligada aos modelos de veículo em que serve. O modelo (marca, modelo e ano) é cadastrado uma vez, e cada veículo de cliente é ligado a um modelo, com placa, cor e quilometragem. Assim o mecânico vê se tem as peças certas antes de começar o serviço e sabe quando precisa encomendar. Se uma peça incompatível for colocada na ordem, o sistema avisa, mas a decisão é do mecânico.

## Documentação

Acesse o [índice da documentação](documentation/documentacao.md) para consultar os requisitos, as regras de negócio e os casos de uso do projeto.

## Declaração de uso de IA

Utilizei o Claude (Anthropic), modelo Claude Sonnet 5.5, em três momentos do trabalho:

- **Revisão de texto e sintaxe:** para checar a redação e a formatação dos textos.
- **Ideias:** para sugerir funcionalidades, requisitos e regras de negócio, que eu avaliei e escolhi conforme o escopo do sistema.
- **Verificação de falhas:** para apontar possíveis erros e inconsistências nos artefatos, que eu analisei depois e só corrigi quando concordei com o apontamento.