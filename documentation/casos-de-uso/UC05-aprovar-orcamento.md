# UC05 – Aprovar orçamento

## Caso de uso
UC05 – Aprovar orçamento

## Ator principal
Cliente

## Atores secundários
Mecânico (registra a decisão manualmente, quando necessário)

## Resumo
Permitir que o cliente analise o orçamento enviado por mensagem automática via WhatsApp e responda com aprovação ou recusa, liberando ou não o início dos serviços. Estende o UC03 Gerenciar ordem de serviço.

## Requisitos relacionados
RF10, RF15 (RN01, RN04, RN07, RN08).

## Pré-condições
Existe uma ordem de serviço do cliente com o orçamento gerado e o status "em orçamento", e o cliente tem WhatsApp cadastrado.

## Pós-condições
Decisão do cliente registrada no orçamento. Se aprovado, a ordem passa para "aprovada", permitindo o início da execução (RN01) e travando novas peças e alterações (RN07). Se recusado, a ordem é cancelada e um novo atendimento exige uma nova ordem de serviço (RN08).

## Fluxo principal
1. O sistema envia ao WhatsApp do cliente uma mensagem automática com o orçamento, com os serviços, as peças e o valor total, com a orientação de como aprovar ou recusar. (RN04)
2. O cliente analisa o orçamento.
3. O cliente responde à mensagem automática e aprova o orçamento.
4. O sistema registra a aprovação recebida por WhatsApp e altera o status da ordem para "aprovada". (RN01)
5. O sistema informa ao cliente, pelo WhatsApp, que o serviço poderá ser iniciado.

## Fluxos alternativos

### FA01
3. Cliente recusa o orçamento
   3.1 O cliente responde à mensagem automática e recusa o orçamento.
   3.2 O sistema registra a recusa e cancela a ordem, devolvendo ao estoque as peças já baixadas (UC03, FA04). (RN08)
   3.3 Um novo atendimento exige uma nova ordem de serviço.

### FA02
3. Cliente adia a decisão
   3.1 O cliente não responde à mensagem automática.
   3.2 O orçamento continua aguardando decisão e pode ser respondido depois.

### FA03
3. Mecânico registra a decisão manualmente
   3.1 O cliente decidiu fora do WhatsApp (por exemplo, no balcão), ou a resposta não pôde ser registrada automaticamente.
   3.2 O mecânico localiza o orçamento e registra a aprovação ou a recusa do cliente.
   3.3 O sistema registra a decisão e segue no passo 4 (aprovação) ou no FA01 (recusa). (RN01)

## Fluxos de exceção

### FE01
1. Mensagem não entregue
   1.1 O WhatsApp do cliente é inválido ou a mensagem não é entregue.
   1.2 O sistema registra a falha de envio, avisa o mecânico e mantém a ordem em "em orçamento".
   1.3 O mecânico registra a decisão do cliente manualmente (FA03).

### FE02
3. Orçamento já decidido
   3.1 O orçamento já foi aprovado ou recusado.
   3.2 O sistema ignora a nova resposta e mantém a decisão registrada.

### FE03
3. Resposta inválida
   3.1 O cliente responde algo que o sistema não reconhece como aprovação ou recusa.
   3.2 O sistema avisa o mecânico e mantém o orçamento aguardando decisão.
   3.3 O mecânico trata o caso e registra a decisão manualmente (FA03).
