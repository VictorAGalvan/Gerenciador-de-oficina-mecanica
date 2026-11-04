| ID | Requisito não funcional | Categoria |
|----|-------------------------|-----------|
| RNF01 | O sistema deve estar disponível durante o horário comercial (8h às 18h), podendo ser desligado nesse período apenas em caso de emergência. | Disponibilidade |
| RNF02 | As manutenções devem ser realizadas fora do horário comercial. | Manutenibilidade |
| RNF03 | Cada instância do sistema deve consumir no máximo 2 GB de RAM e 1 CPU. | Eficiência |
| RNF04 | Cada oficina deve ter uma instância e um banco de dados próprios, sem nunca unificar os dados de oficinas diferentes. | Isolamento de dados |
| RNF05 | As telas principais devem responder em até 3 segundos em uso normal. | Desempenho |
| RNF06 | As operações mais comuns (cadastrar peça, abrir ordem de serviço) devem ser concluídas em até 3 telas, e cada tela deve mostrar só as informações da tarefa atual. | Usabilidade |
| RNF07 | O sistema deve ter dois ambientes de acesso distintos, um para a oficina e outro para o cliente, e cada ambiente deve mostrar apenas as funções do seu público. | Segurança |
| RNF08 | O sistema deve fazer backup automático diário do banco de cada oficina, fora do horário comercial. | Confiabilidade |
| RNF09 | A área do cliente deve funcionar nos navegadores atuais, inclusive no celular. | Compatibilidade |