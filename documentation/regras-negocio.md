| ID | Regra de negócio | Relacionada a |
|----|------------------|---------------|
| RN01 | O serviço só pode ser iniciado depois que o orçamento for aprovado pelo cliente. | RF09, RF10, RF12 |
| RN02 | Uma peça só pode ser adicionada à ordem de serviço se houver quantidade suficiente em estoque. Quando não houver, o sistema deve permitir reservar a peça por meio de uma encomenda, e a ordem de serviço fica aguardando a chegada dela. | RF03, RF07, RF11, RF12 |
| RN03 | Ao adicionar uma peça incompatível com o veículo, o sistema deve avisar, mas a decisão final é do mecânico. | RF04, RF11 |
| RN04 | O cliente só pode visualizar as próprias ordens de serviço e boletos. | RF16, RF17 |