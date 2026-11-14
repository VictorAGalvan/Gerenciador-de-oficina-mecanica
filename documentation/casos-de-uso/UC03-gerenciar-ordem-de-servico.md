# UC03 – Gerenciar ordem de serviço

## Caso de uso
UC03 – Gerenciar ordem de serviço

## Ator principal
Mecânico

## Atores secundários
Cliente (decide sobre o orçamento por meio do UC05)

## Resumo
Abrir a ordem de serviço de um veículo, gerar o orçamento com serviços e peças e acompanhar o status da ordem até a entrega do veículo e o pagamento. As peças são adicionadas pelo UC06 Adicionar peças à ordem, que é incluído por este caso de uso, e o orçamento é estendido pelo UC05 Aprovar orçamento.

## Pré-condições
Cliente e veículo cadastrados (UC01).

## Pós-condições
Ordem de serviço registrada, com orçamento e status atualizados.

## FLUXO PRINCIPAL
### Fluxo principal
1. O mecânico solicita a abertura de uma ordem de serviço.
2. O mecânico localiza o cliente, por nome ou CPF, e seleciona um dos veículos dele. O sistema exibe o veículo e o seu modelo.
3. O mecânico descreve os serviços a executar.
4. O sistema registra a ordem de serviço com o status "aberta".
5. O mecânico adiciona à ordem as peças necessárias. (include UC06)
6. O mecânico informa os valores dos serviços e confere os preços das peças (preenchidos com o preço do cadastro), e o sistema gera o orçamento da ordem, alterando o status para "aguardando aprovação".
7. O cliente analisa o orçamento e informa sua decisão. (extend UC05)
8. Com a ordem "aprovada" (UC05), o mecânico atualiza o status para "em execução". (RN01)
9. Concluídos os serviços, o mecânico atualiza o status para "concluída", e as encomendas da ordem passam a ser consideradas concluídas.
10. Ao devolver o veículo ao cliente, o mecânico atualiza o status para "entregue".
11. Se o cliente não pagou na entrega, o mecânico atualiza o status para "não paga"; ao receber o pagamento, feito fora do sistema, atualiza para "paga".

## FLUXOS ALTERNATIVOS
### FA01
2. Cliente ou veículo não localizado
   2.1 O cliente ou o veículo não é localizado.
   2.2 Executa-se Cadastrar clientes e veículos (UC01) e o fluxo retorna ao passo 2.

### FA02
7. Orçamento recusado ou ordem cancelada antes da aprovação (RN07, RN08)
   7.1 O cliente recusa o orçamento (UC05) ou desiste do serviço antes da aprovação.
   7.2 Na recusa, o sistema cancela a ordem automaticamente; na desistência, o mecânico cancela a ordem.
   7.3 O sistema altera o status para "cancelada", devolve ao estoque as peças já baixadas e registra a entrada de cada uma. (RN02)
   7.4 Para retomar o atendimento, o mecânico abre uma nova ordem de serviço. (RN08)

### FA03
1. Consultar e atualizar o status
   1.1 O mecânico localiza a ordem por cliente, veículo ou status.
   1.2 O sistema exibe os dados da ordem e o status atual.
   1.3 O mecânico altera o status para uma das transições permitidas (1.4) e o sistema registra a mudança.
   1.4 Transições permitidas: aberta → aguardando aprovação, aguardando peça ou cancelada; aguardando peça → aberta ou cancelada; aguardando aprovação → aprovada, cancelada ou aberta (para gerar novo orçamento, UC06 FA03); aprovada → em execução; em execução → concluída; concluída → entregue; entregue → não paga ou paga; não paga → paga. As ordens "paga" e "cancelada" não mudam mais. (RF12, RN07)

## FLUXOS DE EXCEÇÃO
### FE01
8. Início da execução não permitido (RN01, RN02)
   8.1 O mecânico tenta passar a ordem para "em execução" sem o orçamento aprovado ou com peças encomendadas ainda não recebidas.
   8.2 O sistema não permite a alteração e mantém o status atual.

### FE02
1. Transição inválida ou ordem encerrada (FA03)
   1.1 O status escolhido não é uma transição permitida, ou a ordem já está "paga" ou "cancelada" e não pode ser alterada.
   1.2 O sistema recusa a alteração e mantém o status atual.

### FE03
6. Cancelamento ou alteração de valores em ordem já aprovada (RN07)
   6.1 O mecânico tenta cancelar uma ordem ou alterar valores de uma ordem cujo orçamento já foi aprovado.
   6.2 O sistema recusa a alteração, informa que um acréscimo exige uma nova ordem de serviço e mantém o status atual.
