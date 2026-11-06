| ID | Requisito funcional |
|----|---------------------|
| RF01 | O sistema deve permitir cadastrar, editar, consultar e inativar clientes (nome, CPF único, telefone, WhatsApp). |
| RF02 | O sistema deve permitir cadastrar, editar e consultar modelos de veículo (marca, modelo, ano) e veículos de clientes (modelo, placa única, cor, quilometragem), vinculando cada veículo a um cliente e listando os veículos de um cliente. |
| RF03 | O sistema deve permitir cadastrar, editar e consultar peças (código, nome, categoria, preço, quantidade em estoque, estoque mínimo). |
| RF04 | O sistema deve permitir vincular uma peça a um ou mais modelos de veículo compatíveis. |
| RF05 | O sistema deve listar as peças compatíveis com o modelo ao consultar um veículo ou um modelo de veículo. |
| RF06 | O sistema deve listar os clientes que possuem veículos de modelos compatíveis ao consultar uma peça. |
| RF07 | O sistema deve registrar entradas e saídas de estoque, guardando data, quantidade, motivo e responsável. |
| RF08 | O sistema deve permitir abrir uma ordem de serviço vinculando cliente, veículo e descrição dos serviços a executar. |
| RF09 | O sistema deve permitir gerar um orçamento vinculado à ordem de serviço, com serviços e peças. |
| RF10 | O sistema deve permitir registrar a aprovação ou recusa do orçamento pelo cliente por meio de mensagens automáticas no WhatsApp. |
| RF11 | O sistema deve permitir adicionar peças à ordem de serviço, dando baixa automática no estoque, ou registrar a encomenda da peça quando não houver estoque suficiente, e devolver ao estoque as peças da ordem quando ela for cancelada. |
| RF12 | O sistema deve permitir que a oficina atualize a ordem conforme o serviço avança, usando os status aberta, em orçamento, aprovada, aguardando peça, em execução, concluída, entregue e cancelada. Só é possível iniciar o serviço depois da aprovação do orçamento e da chegada das peças encomendadas. Uma ordem entregue ou cancelada não pode ser alterada. |
| RF13 | O sistema deve permitir agendar atendimentos com data, horário, cliente, veículo e serviço, e visualizá-los em um calendário. |
| RF14 | O sistema deve permitir cadastrar uma cobrança da ordem de serviço com valor e vencimento. Depois de receber a confirmação do pagamento, o mecânico pode registrar o valor, a forma e a data do recebimento. O pagamento acontece fora do sistema. |
| RF15 | O sistema deve permitir que o cliente acesse sua área com login por CPF e senha. |
| RF16 | O sistema deve permitir que o cliente acompanhe o status das suas ordens de serviço. |
| RF17 | Na área do cliente, o sistema deve mostrar as cobranças da própria ordem e se estão em aberto ou pagas. O pagamento é feito fora do sistema e sua confirmação é registrada pelo mecânico. |
| RF18 | O sistema deve gerar relatórios de clientes, veículos, estoque e ordens de serviço. |