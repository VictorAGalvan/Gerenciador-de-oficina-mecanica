# UC04 – Verificar estoque

## Caso de uso
UC04 – Verificar estoque

## Ator principal
Mecânico (por meio do UC03)

## Atores secundários
-

## Resumo
Verificar se a peça escolhida para a ordem de serviço tem quantidade suficiente em estoque e se é compatível com o modelo do veículo da ordem, devolvendo o resultado ao caso de uso que o chamou. É incluído pelo UC03 Gerenciar ordem de serviço.

## Requisitos relacionados
RF04, RF11 (RN02, RN03).

## Pré-condições
Existe uma ordem de serviço aberta, com veículo informado, e uma peça selecionada pelo mecânico (UC03).

## Pós-condições
Resultado da verificação (disponível e compatível, estoque insuficiente ou incompatível) devolvido ao UC03. Este caso de uso não altera o estoque.

## FLUXO PRINCIPAL
### Fluxo principal
1. O sistema recebe a peça selecionada e a quantidade pretendida para a ordem.
2. O sistema consulta a quantidade da peça em estoque.
3. O sistema compara a quantidade em estoque com a pretendida. (RN02)
4. O sistema verifica se a peça é compatível com o modelo do veículo da ordem. (RN03)
5. O sistema informa que a peça está disponível e é compatível, e retorna ao UC03.

## FLUXOS ALTERNATIVOS
### FA01
3. Estoque insuficiente (RN02)
   3.1 A quantidade em estoque é menor que a pretendida.
   3.2 O sistema informa a quantidade disponível, verifica também a compatibilidade (passo 4) e retorna ao UC03 indicando a falta e, se houver, a incompatibilidade (UC03, FA02 e FA03).

### FA02
4. Peça incompatível (RN03)
   4.1 A peça não está vinculada ao modelo do veículo da ordem.
   4.2 O sistema retorna ao UC03 indicando a incompatibilidade, para o mecânico decidir (UC03, FA03).

## FLUXOS DE EXCEÇÃO
### FE01
2. Peça não encontrada
   2.1 A peça selecionada não existe no cadastro de peças.
   2.2 O sistema informa o erro e retorna ao UC03 sem concluir a verificação.
