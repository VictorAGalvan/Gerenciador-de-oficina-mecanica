| ID | Requisito funcional |
|----|---------------------|
| RF01 | O sistema deve permitir cadastrar, editar, consultar e inativar clientes (nome, CPF, telefone, e-mail). |
| RF02 | O sistema deve permitir cadastrar, editar e consultar veículos (placa, marca, modelo, ano, cor, quilometragem), vinculando cada veículo a um cliente e listando os veículos de um cliente. |
| RF03 | O sistema deve permitir cadastrar, editar e consultar peças (código, nome, categoria, preço, quantidade em estoque, estoque mínimo). |
| RF04 | O sistema deve permitir vincular uma peça a um ou mais veículos compatíveis (marca, modelo, ano). |
| RF05 | O sistema deve listar as peças compatíveis ao consultar um veículo. |
| RF06 | O sistema deve listar os clientes que possuem veículos compatíveis ao consultar uma peça. |
| RF07 | O sistema deve registrar entradas e saídas de estoque, guardando data, quantidade, motivo e responsável. |
| RF08 | O sistema deve permitir abrir uma ordem de serviço vinculando cliente, veículo e descrição dos serviços a executar. |
| RF09 | O sistema deve permitir gerar um orçamento vinculado à ordem de serviço, com serviços e peças. |
| RF10 | O sistema deve permitir registrar a aprovação ou recusa do orçamento pelo cliente. |
| RF11 | O sistema deve permitir adicionar peças à ordem de serviço, dando baixa automática no estoque, ou registrar a encomenda da peça quando não houver estoque suficiente, e devolver ao estoque as peças da ordem quando ela for cancelada. |
| RF12 | O sistema deve permitir atualizar o status da ordem de serviço (aberta, em orçamento, aprovada, aguardando peça, em execução, concluída, entregue, cancelada), respeitando as transições válidas definidas no diagrama de estados. |
| RF13 | O sistema deve permitir agendar atendimentos com data, horário, cliente, veículo e serviço, e visualizá-los em um calendário. |
| RF14 | O sistema deve gerar o boleto da ordem de serviço (valor e vencimento) e registrar seu pagamento (valor, forma, data e situação), sem integração com serviços bancários. |
| RF15 | O sistema deve permitir que o cliente acesse sua área com login por CPF e senha. |
| RF16 | O sistema deve permitir que o cliente acompanhe o status das suas ordens de serviço. |
| RF17 | O sistema deve permitir que o cliente consulte seus boletos e realize o pagamento pela área do cliente, sendo o pagamento apenas registrado no sistema, sem integração bancária. |
| RF18 | O sistema deve gerar relatórios de clientes, veículos, estoque e ordens de serviço. |