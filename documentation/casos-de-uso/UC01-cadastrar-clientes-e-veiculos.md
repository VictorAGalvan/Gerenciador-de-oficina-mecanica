# UC01 – Cadastrar clientes e veículos

## Caso de uso
UC01 – Cadastrar clientes e veículos

## Ator principal
Mecânico

## Atores secundários
-

## Resumo
Cadastrar e manter os dados dos clientes, dos modelos de veículo (marca, modelo e ano, cadastrados uma só vez) e dos veículos de cada cliente (placa, cor e quilometragem), que servem de base para as ordens de serviço e para a compatibilidade com as peças.

## Pré-condições
O mecânico acessou o ambiente da oficina.

## Pós-condições
Cliente e veículo registrados (ou alterados), com o veículo vinculado ao cliente e a um modelo, prontos para uso em uma ordem de serviço.

## FLUXO PRINCIPAL
### Fluxo principal
1. O mecânico solicita o cadastro de um novo cliente.
2. O sistema apresenta o formulário de cadastro de cliente.
3. O mecânico informa nome, CPF, telefone e WhatsApp.
4. O sistema valida os dados e registra o cliente.
5. O mecânico solicita o cadastro de um veículo do cliente.
6. O sistema apresenta o formulário de cadastro de veículo, com a lista de modelos cadastrados.
7. O mecânico seleciona o modelo e informa placa, cor e quilometragem.
8. O sistema valida os dados, registra o veículo e o vincula ao cliente e ao modelo.
9. O sistema exibe o cliente com a lista de seus veículos.

## FLUXOS ALTERNATIVOS
### FA01
1. Cliente já cadastrado
   1.1 O mecânico busca o cliente por nome ou CPF e o sistema o localiza.
   1.2 O fluxo segue no passo 5.

### FA02
1. Alterar cliente, veículo ou modelo
   1.1 O mecânico localiza o cliente, o veículo ou o modelo, altera os dados e confirma.
   1.2 O sistema valida e registra a alteração.

### FA03
1. Consultar clientes, veículos e modelos
   1.1 O mecânico informa o critério de busca (nome, CPF, placa, marca ou modelo) e o sistema exibe os registros correspondentes.
   1.2 Ao selecionar um cliente, o sistema lista os veículos vinculados a ele.

### FA04
7. Modelo de veículo não cadastrado
   7.1 O modelo do veículo não existe na lista.
   7.2 O mecânico cadastra o modelo, informando marca, modelo e ano, e o fluxo retorna ao passo 7.

## FLUXOS DE EXCEÇÃO
### FE01
4. CPF já cadastrado ou dados inválidos (RN05)
   4.1 O CPF já existe no sistema ou há campo obrigatório não preenchido.
   4.2 O sistema informa o problema e retorna ao formulário.

### FE02
7. Modelo já cadastrado ou dados inválidos (FA04)
   7.1 Já existe um modelo com a mesma marca, modelo e ano, ou há campo obrigatório não preenchido.
   7.2 O sistema informa o problema e retorna ao cadastro do modelo.

### FE03
8. Placa já cadastrada ou dados inválidos (RN06)
   8.1 A placa já existe no sistema ou há campo obrigatório não preenchido.
   8.2 O sistema informa o problema e retorna ao formulário.
