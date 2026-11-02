| ID | Regra de negócio | Relacionada a |
|----|------------------|---------------|
| RN01 | O serviço só pode ser iniciado depois que o orçamento for aprovado pelo cliente, ou seja, a ordem de serviço só pode passar para o status "em execução" após a aprovação. | RF09, RF10, RF12 |
| RN02 | A baixa no estoque ocorre quando a peça é adicionada à ordem de serviço, e isso só é permitido se houver quantidade suficiente. Quando não houver, o sistema deve permitir registrar a encomenda da peça, e a ordem fica com o status "aguardando peça" até a chegada dela. Se a ordem for cancelada, as peças já baixadas retornam ao estoque. | RF03, RF07, RF11, RF12 |
| RN03 | Ao adicionar uma peça incompatível com o veículo, o sistema deve avisar, mas a decisão final é do mecânico. | RF04, RF11 |
| RN04 | O cliente só pode visualizar as próprias ordens de serviço e boletos. | RF16, RF17 |