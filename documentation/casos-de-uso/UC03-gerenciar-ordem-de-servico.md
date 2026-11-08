# UC03 – Gerenciar ordem de serviço

## Caso de uso
UC03 – Gerenciar ordem de serviço

## Ator principal
Mecânico

## Atores secundários
Cliente (decide sobre o orçamento por meio do UC05)

## Resumo
Abrir a ordem de serviço de um veículo, gerar o orçamento com serviços e peças, adicionar as peças usadas dando baixa no estoque (ou encomendando as que faltam) e acompanhar o status da ordem até a entrega do veículo. Também agenda atendimentos, registra a cobrança da ordem e gera relatórios de ordens de serviço. Inclui o UC04 Verificar estoque e é estendido pelo UC05 Aprovar orçamento.

## Requisitos relacionados
RF08, RF09, RF11, RF12, RF13, RF14, RF16, RF17, RF18 (RN01, RN02, RN03, RN04, RN07, RN08).

## Pré-condições
Cliente (ativo) e veículo cadastrados (UC01).

## Pós-condições
Ordem de serviço registrada, com orçamento, peças e status atualizados; estoque ajustado conforme as peças usadas.

## FLUXO PRINCIPAL
### Fluxo principal
1. O mecânico solicita a abertura de uma ordem de serviço.
2. O mecânico localiza o veículo e o sistema exibe o veículo, seu modelo e o cliente vinculado.
3. O mecânico descreve os serviços a executar.
4. O sistema registra a ordem de serviço com o status "aberta".
5. O mecânico adiciona à ordem as peças necessárias, informando a quantidade de cada uma. As peças só podem ser adicionadas enquanto o orçamento não foi aprovado; se já houver orçamento gerado, é preciso gerar um novo (FA09). (RN07)
6. O sistema verifica a quantidade em estoque e a compatibilidade da peça com o modelo do veículo. (include UC04)
7. O sistema registra a peça na ordem, dá baixa no estoque e registra a saída com data, quantidade e motivo. (RN02)
8. O mecânico informa os valores dos serviços e confere os preços das peças (preenchidos com o preço do cadastro), e o sistema gera o orçamento da ordem, alterando o status para "em orçamento".
9. O cliente analisa o orçamento e informa sua decisão. (extend UC05)
10. Com a ordem "aprovada" (UC05), o mecânico atualiza o status para "em execução". (RN01)
11. Concluídos os serviços, o mecânico atualiza o status para "concluída", e as encomendas da ordem passam a ser consideradas concluídas.
12. Ao devolver o veículo ao cliente, o mecânico atualiza o status para "entregue".
13. A cada mudança de status dos passos anteriores, o sistema avisa o cliente pelo WhatsApp. (RF16, RN04)

## FLUXOS ALTERNATIVOS
### FA01
2. Veículo não cadastrado
   2.1 O veículo ou o cliente não é localizado.
   2.2 Executa-se Cadastrar clientes e veículos (UC01) e o fluxo retorna ao passo 2.

### FA02
6. Peça sem estoque suficiente (RN02)
   6.1 O sistema informa que a quantidade em estoque é insuficiente.
   6.2 O mecânico registra a encomenda da peça, vinculada à ordem (peça e quantidade).
   6.3 O sistema altera o status da ordem para "aguardando peça".
   6.4 Quando a peça chega, o mecânico registra a entrada no estoque (UC02), a ordem volta ao status "aberta" e o fluxo retoma no passo 6.

### FA03
6. Peça incompatível com o modelo do veículo (RN03)
   6.1 O sistema avisa que a peça não é compatível com o modelo do veículo.
   6.2 O mecânico decide: se mantiver a peça, o fluxo segue no passo 7; se não, escolhe outra peça no passo 5.

### FA04
9. Orçamento recusado ou ordem cancelada antes da aprovação (RN07, RN08)
   9.1 O cliente recusa o orçamento (UC05) ou desiste do serviço antes da aprovação.
   9.2 Na recusa, o sistema cancela a ordem automaticamente; na desistência, o mecânico cancela a ordem.
   9.3 O sistema altera o status para "cancelada", devolve ao estoque as peças já baixadas e registra a entrada de cada uma. (RN02)
   9.4 Para retomar o atendimento, o mecânico abre uma nova ordem de serviço. (RN08)

### FA05
1. Consultar e atualizar o status
   1.1 O mecânico localiza a ordem por cliente, veículo ou status.
   1.2 O sistema exibe os dados da ordem e o status atual.
   1.3 O mecânico altera o status para uma das transições permitidas (1.4) e o sistema registra a mudança.
   1.4 Transições permitidas: aberta → em orçamento, aguardando peça ou cancelada; aguardando peça → aberta ou cancelada; em orçamento → aprovada, cancelada ou aberta (para gerar novo orçamento, FA09); aprovada → em execução; em execução → concluída; concluída → entregue. As ordens "entregue" e "cancelada" não mudam mais. (RF12, RN07)

### FA06
1. Agendar atendimento
   1.1 O mecânico solicita um novo agendamento e informa data, horário, cliente, veículo e serviço.
   1.2 O sistema valida os dados e registra o agendamento.
   1.3 O mecânico visualiza os atendimentos agendados em um calendário.

### FA07
1. Registrar cobrança e pagamento (opcional)
   1.1 Concluídos os serviços (passo 11), o mecânico decide se cadastra uma cobrança para a ordem. Se sim, informa valor e vencimento.
   1.2 O sistema registra a cobrança com o status "em aberto" e a envia ao WhatsApp do cliente, com valor e vencimento. (RN04)
   1.3 O cliente paga fora do sistema.
   1.4 Ao receber a confirmação do pagamento, o mecânico registra o valor, a forma e a data do recebimento, e o sistema altera a cobrança para "paga".
   1.5 A entrega do veículo (passo 12) não depende do pagamento: a ordem pode ser entregue com a cobrança em aberto.

### FA08
1. Gerar relatório de ordens de serviço
   1.1 O mecânico solicita o relatório de ordens de serviço e informa o filtro, se houver (cliente, veículo ou status).
   1.2 O sistema gera o relatório com as ordens correspondentes.

### FA09
5. Adicionar peça com orçamento já gerado (RN07)
   5.1 A ordem está "em orçamento" e o mecânico precisa adicionar uma peça.
   5.2 O sistema volta a ordem para "aberta" e o orçamento anterior perde a validade.
   5.3 O fluxo segue no passo 5; ao gerar o novo orçamento (passo 8), ele é enviado ao cliente para nova decisão (UC05).

## FLUXOS DE EXCEÇÃO
### FE01
10. Início da execução não permitido (RN01, RF12)
   10.1 O mecânico tenta passar a ordem para "em execução" sem o orçamento aprovado ou com peças encomendadas ainda não recebidas.
   10.2 O sistema não permite a alteração e mantém o status atual.

### FE02
1. Transição inválida ou ordem encerrada (FA05)
   1.1 O status escolhido não é uma transição permitida, ou a ordem já está "entregue" ou "cancelada" e não pode ser alterada.
   1.2 O sistema recusa a alteração e mantém o status atual.

### FE03
5. Alteração em ordem já aprovada (RN07)
   5.1 O mecânico tenta adicionar peça, alterar valores ou cancelar uma ordem cujo orçamento já foi aprovado.
   5.2 O sistema recusa a alteração, informa que um acréscimo exige uma nova ordem de serviço e mantém o status atual.
