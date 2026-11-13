| ID | Requisito funcional |
|----|---------------------|
| RF01 | O sistema deve permitir cadastrar, editar e consultar clientes (nome, CPF único, telefone, WhatsApp). |
| RF02 | O sistema deve permitir cadastrar, editar e consultar modelos de veículo (marca, modelo, ano) e veículos de clientes (modelo, placa única, cor, quilometragem), vinculando cada veículo a um cliente e listando os veículos de um cliente. |
| RF03 | O sistema deve permitir cadastrar, editar e consultar peças (código, nome, categoria, preço, quantidade em estoque, estoque mínimo). O sistema deve avisar o mecânico quando a quantidade em estoque de uma peça ficar igual ou abaixo do estoque mínimo. |
| RF04 | O sistema deve permitir vincular uma peça a um ou mais modelos de veículo compatíveis. |
| RF05 | O sistema deve listar as peças compatíveis com o modelo ao consultar um veículo ou um modelo de veículo. |
| RF06 | O sistema deve listar os clientes que possuem veículos de modelos compatíveis ao consultar uma peça. |
| RF07 | O sistema deve registrar entradas e saídas de estoque, guardando data, quantidade e motivo. |
| RF08 | O sistema deve permitir abrir uma ordem de serviço vinculando cliente, veículo e descrição dos serviços a executar. |
| RF09 | O sistema deve permitir gerar um orçamento vinculado à ordem de serviço, com serviços e peças. Enquanto não for aprovado, o orçamento pode ser refeito, e o novo substitui o anterior. |
| RF10 | O sistema deve permitir registrar a aprovação ou recusa do orçamento pelo cliente por meio de mensagens automáticas no WhatsApp. Se a resposta for inválida ou a mensagem não for entregue, o sistema avisa o mecânico, que registra a decisão manualmente. |
| RF11 | O sistema deve permitir adicionar peças à ordem de serviço, dando baixa automática no estoque, ou registrar a encomenda da peça quando não houver estoque suficiente, e devolver ao estoque as peças da ordem quando ela for cancelada. A encomenda fica vinculada à ordem e é considerada concluída quando a ordem é concluída. |
| RF12 | O sistema deve permitir que a oficina atualize o status da ordem de serviço conforme o serviço avança (aberta, aguardando aprovação, aprovada, aguardando peça, em execução, concluída, entregue, não paga, paga e cancelada). |
