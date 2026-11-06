| ID | Regra de negócio | Relacionada a |
|----|------------------|---------------|
| RN01 | O serviço só pode ser iniciado depois que o cliente aceitar o orçamento pelo WhatsApp, e a ordem só pode passar para "em execução" após essa aprovação. | RF09, RF10, RF12 |
| RN02 | A baixa no estoque ocorre quando a peça é adicionada à ordem e só é permitida se houver quantidade suficiente. Sem estoque, deve ser possível registrar uma encomenda, e a ordem fica "aguardando peça" até sua chegada. Se a ordem for cancelada, as peças baixadas retornam ao estoque. | RF03, RF07, RF11, RF12 |
| RN03 | Ao adicionar uma peça incompatível com o veículo, o sistema deve avisar, mas a decisão final é do mecânico. | RF04, RF11 |
| RN04 | O cliente só pode visualizar as próprias ordens de serviço e boletos. | RF16, RF17 |
| RN05 | O CPF do cliente deve ser único no sistema, não pode haver dois clientes com o mesmo número. | RF01 |
| RN06 | A placa do veículo deve ser única no sistema, não pode haver dois veículos cadastrados com a mesma placa. | RF02 |