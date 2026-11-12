# UC02 – Controlar estoque de peças

## Caso de uso
UC02 – Controlar estoque de peças

## Ator principal
Mecânico

## Atores secundários
-

## Resumo
Manter o cadastro das peças e controlar a quantidade em estoque, registrando entradas e saídas e vinculando cada peça aos modelos de veículo compatíveis, para que o mecânico saiba o que está disponível e o que precisa ser encomendado. Também gera o relatório de estoque.

## Pré-condições
O mecânico acessou o ambiente da oficina.
Os modelos de veículo compatíveis com a peça estão cadastrados (UC01).

## Pós-condições
Peça cadastrada ou atualizada, com a quantidade em estoque e os modelos compatíveis registrados; movimentações de estoque registradas com data, quantidade e motivo.

## FLUXO PRINCIPAL
### Fluxo principal
1. O mecânico solicita o cadastro de uma peça.
2. O sistema apresenta o formulário de cadastro de peça.
3. O mecânico informa código, nome, categoria, preço, quantidade em estoque e estoque mínimo.
4. O sistema valida os dados e registra a peça.
5. O mecânico seleciona os modelos de veículo compatíveis com a peça.
6. O sistema registra a compatibilidade entre a peça e os modelos selecionados.
7. O sistema registra a entrada inicial no estoque, com data, quantidade e motivo.

## FLUXOS ALTERNATIVOS
### FA01
1. Registrar entrada de peças
   1.1 O mecânico localiza a peça e informa a quantidade recebida e o motivo (compra ou chegada de encomenda).
   1.2 O sistema soma a quantidade ao estoque e registra a movimentação.
   1.3 Se houver ordem de serviço aguardando a peça, o mecânico pode retomá-la (UC03).

### FA02
1. Registrar saída de peças
   1.1 O mecânico localiza a peça e informa a quantidade e o motivo da saída.
   1.2 O sistema subtrai a quantidade do estoque e registra a movimentação.

### FA03
1. Alterar peça
   1.1 O mecânico localiza a peça, altera os dados ou os modelos compatíveis e confirma. A quantidade em estoque não é editada aqui: só muda por entrada ou saída.
   1.2 O sistema valida e registra a alteração.

### FA04
1. Consultar peças compatíveis com um veículo ou modelo
   1.1 O mecânico informa ou seleciona o veículo ou o modelo.
   1.2 O sistema identifica o modelo e lista as peças compatíveis, com a quantidade em estoque de cada uma.

### FA05
1. Consultar clientes com veículos compatíveis
   1.1 O mecânico seleciona uma peça.
   1.2 O sistema lista os clientes que possuem veículos de modelos compatíveis com ela.

### FA06
1. Gerar relatório de estoque
   1.1 O mecânico solicita o relatório de estoque e informa o filtro, se houver (por exemplo, categoria ou peças abaixo do estoque mínimo).
   1.2 O sistema gera o relatório com as peças e as quantidades em estoque.

### FA07
1. Aviso de estoque mínimo
   1.1 Ao registrar uma saída (FA02) ou ao dar baixa por uma ordem de serviço (UC03), o sistema compara a quantidade em estoque com o estoque mínimo da peça.
   1.2 Se a quantidade ficar igual ou abaixo do mínimo, o sistema avisa o mecânico para que ele providencie a reposição.

## FLUXOS DE EXCEÇÃO
### FE01
4. Código já cadastrado ou dados inválidos
   4.1 O código da peça já existe, há campo obrigatório vazio ou o preço é negativo.
   4.2 O sistema informa o problema e retorna ao formulário.

### FE02
1. Saída maior que o estoque (FA02)
   1.1 A quantidade informada é maior que a disponível.
   1.2 O sistema recusa a saída e informa a quantidade em estoque.