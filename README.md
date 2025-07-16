# Sistema de Controle de Ordens de Serviço para Oficina Mecânica

## 📌 Descrição do Projeto

Este projeto apresenta um modelo conceitual para um sistema de controle e gerenciamento de ordens de serviço (OS) em uma **oficina mecânica**, elaborado com base em uma narrativa proposta para um desafio de modelagem de dados.

O modelo foi desenvolvido considerando os principais processos de uma oficina, incluindo o atendimento ao cliente, recebimento e avaliação de veículos, emissão de ordens de serviço, execução de serviços por equipes de mecânicos, e cálculo dos custos com peças e mão-de-obra.

## 🎯 Objetivo

Criar um esquema conceitual do zero para representar as entidades, relacionamentos e atributos envolvidos no contexto de uma oficina mecânica.

---

## 🧾 Narrativa Fornecida

> Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica.
>
> - Clientes levam veículos à oficina para conserto ou revisão.
> - Cada veículo é designado a uma equipe de mecânicos.
> - A equipe identifica os serviços e preenche a OS com data de entrega.
> - O valor dos serviços é calculado com base em uma tabela de mão-de-obra.
> - O valor das peças também compõe a OS.
> - O cliente autoriza a execução dos serviços.
> - A mesma equipe avalia e executa os serviços.
> - Cada mecânico tem código, nome, endereço e especialidade.
> - Cada OS tem número, data de emissão, valor total, status e data de conclusão.

---

## 📐 Modelo Conceitual (Entidades e Relacionamentos)

### 🧍 Cliente
- **id_cliente** (PK)
- nome
- telefone
- e-mail
- endereço

### 🚗 Veículo
- **id_veiculo** (PK)
- placa
- modelo
- marca
- ano
- id_cliente (FK)

### 🧑‍🔧 Mecânico
- **id_mecanico** (PK)
- nome
- endereço
- especialidade

### 👨‍🔧 Equipe
- **id_equipe** (PK)
- nome_equipe (opcional)

### 🔧 Equipe_Mecanico (Relacionamento N:N)
- **id_equipe** (FK)
- **id_mecanico** (FK)

### 📄 OrdemServico
- **id_os** (PK)
- data_emissao
- data_conclusao
- valor_total
- status
- id_veiculo (FK)
- id_equipe (FK)
- autorizada (booleano)

### 🛠️ Servico
- **id_servico** (PK)
- nome_servico
- descricao
- valor_mao_obra

### 🧾 OS_Servico (Relacionamento N:N)
- **id_os** (FK)
- **id_servico** (FK)
- quantidade
- subtotal

### 🧩 Peca
- **id_peca** (PK)
- nome
- valor_unitario
- descricao

### 🔗 OS_Peca (Relacionamento N:N)
- **id_os** (FK)
- **id_peca** (FK)
- quantidade
- subtotal

---

## 🧠 Observações

- O modelo considera que uma OS pode conter **vários serviços e peças**.
- Uma **equipe pode conter vários mecânicos**, e um mecânico pode participar de várias equipes (N:N).
- A **autorização do cliente** está registrada como um campo booleano (`autorizada`) na OS.
- O valor total da OS pode ser calculado somando os subtotais de peças e serviços.

---

## 🖼️ Imagem do DER (Opcional)

Você pode adicionar um DER (Diagrama Entidade-Relacionamento) com base nesse modelo. Sugestão de ferramenta: [dbdiagram.io](https://dbdiagram.io), [draw.io](https://draw.io) ou [MySQL Workbench].

---

## 🚀 Como usar

Este projeto é apenas conceitual. Você pode usar o modelo como base para:

- Criação de scripts SQL (DDL)
- Geração de diagramas físicos
- Implementações em sistemas reais de oficinas mecânicas

---

## 🧑‍💻 Autor

Desenvolvido por [Seu Nome Aqui].

---

## 📝 Licença

Este projeto está sob a licença MIT.
