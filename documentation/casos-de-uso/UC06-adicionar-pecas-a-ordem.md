# UC06 – Adicionar peças à ordem

## Caso de uso
UC06 – Adicionar peças à ordem

## Ator principal
Mecânico (por meio do UC03)

## Atores secundários
-

## Resumo
Adicionar à ordem de serviço as peças necessárias, verificando o estoque e a compatibilidade, dando baixa no estoque ou registrando a encomenda das que faltam. É incluído pelo UC03 Gerenciar ordem de serviço e inclui o UC04 Verificar estoque.

## Pré-condições
Existe uma ordem de serviço cujo orçamento ainda não foi aprovado (UC03).

## Pós-condições
Peças registradas na ordem, com a baixa no estoque e a saída registrada com data, quantidade e motivo, ou encomenda registrada para as peças sem estoque suficiente.

## FLUXO PRINCIPAL
### Fluxo principal
1. O mecânico seleciona a peça e informa a quantidade necessária.
2. O sistema verifica a quantidade em estoque e a compatibilidade da peça com o modelo do veículo. (include UC04)
3. O sistema registra a peça na ordem, dá baixa no estoque e registra a saída com data, quantidade e motivo. (RN02)
4. O mecânico repete os passos 1 a 3 para as demais peças ou conclui a adição de peças.

## FLUXOS ALTERNATIVOS
### FA01
2. Peça sem estoque suficiente (RN02)
   2.1 O sistema informa que a quantidade em estoque é insuficiente.
   2.2 O mecânico registra a encomenda da peça, vinculada à ordem (peça e quantidade).
   2.3 O sistema altera o status da ordem para "aguardando peça".
   2.4 Quando a peça chega, o mecânico registra a entrada no estoque (UC02), a ordem volta ao status "aberta" e o fluxo retoma no passo 2.

### FA02
2. Peça incompatível com o modelo do veículo (RN03)
   2.1 O sistema avisa que a peça não é compatível com o modelo do veículo.
   2.2 O mecânico decide: se mantiver a peça, o fluxo segue no passo 3; se não, escolhe outra peça no passo 1.

### FA03
1. Adicionar peça com orçamento já gerado (RN07)
   1.1 A ordem está "aguardando aprovação" e o mecânico precisa adicionar uma peça.
   1.2 O sistema volta a ordem para "aberta" e o orçamento anterior perde a validade.
   1.3 O fluxo segue no passo 1; ao gerar o novo orçamento (UC03, passo 6), ele é enviado ao cliente para nova decisão (UC05).

## FLUXOS DE EXCEÇÃO
### FE01
1. Ordem já aprovada (RN07)
   1.1 O mecânico tenta adicionar uma peça a uma ordem cujo orçamento já foi aprovado.
   1.2 O sistema recusa, informa que um acréscimo exige uma nova ordem de serviço e mantém o status atual.
