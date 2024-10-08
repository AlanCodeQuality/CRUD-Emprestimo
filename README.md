# Sistema de Gerenciamento de Empréstimos

Este projeto é um sistema para gerenciamento de empréstimos de carros, oferecendo funcionalidades como cadastro de usuários, cadastro de veículos (itens de empréstimo) e gerenciamento dos empréstimos.

## Estrutura do Projeto 

![image](https://github.com/user-attachments/assets/8e18e266-c431-420d-abee-46333e51a31c)


## Funcionalidades

- **Cadastro de Clientes:** Adicionar, atualizar, selecionar e deletar clientes no sistema.
- **Cadastro de Veículos (Itens para Empréstimo):** Adicionar, atualizar, selecionar e deletar veículos disponíveis para empréstimo.
- **Gerenciamento de Empréstimos:** Controlar os empréstimos, incluindo o registro de novas transações, atualização de informações, devoluções e consulta de histórico.
- **Serviços HTTPS:** O servidor também suporta a execução segura via HTTPS.

## Tecnologias Utilizadas

- **Node.js**: Ambiente de execução para o JavaScript no servidor.
- **Express.js**: Framework para construir a API REST.
- **SQLite**: Banco de dados utilizado para armazenar informações de clientes, veículos e empréstimos.
- **Body-parser**: Middleware para parsing de requisições HTTP.
- **Cors**: Middleware para habilitar o CORS (Cross-Origin Resource Sharing).
- **HTTPS**: Servidor rodando com certificados SSL para comunicação segura.

# Execução do Projeto

## Pré-requisitos
- Node.js
- SQLite

## Instalação
1. Clone o repositório do projeto.
2. Instale as dependências utilizando o comando:
   ```bash
   npm install

# Inicialização do Banco de Dados

A função `initializeDatabase()` no arquivo `createTable.js` será executada ao iniciar o servidor, criando as seguintes tabelas:

- **clientes**: Armazena os dados dos clientes (nome, CPF, endereço, etc.).
- **veiculos**: Armazena as informações dos veículos (modelo, marca, ano de fabricação, etc.).
- **emprestimos**: Registra os empréstimos feitos, associando clientes e veículos.

O banco será populado com alguns dados iniciais para facilitar os testes.

## API Endpoints

### Clientes
- `GET /clientes` - Lista todos os clientes
- `GET /cliente` - Busca um cliente pelo ID
- `POST /clientes` - Adiciona um novo cliente
- `PUT /cliente` - Atualiza um cliente existente
- `DELETE /cliente` - Remove um cliente pelo ID

### Veículos
- `GET /veiculos` - Lista todos os veículos
- `GET /veiculos` - Busca um veículo pelo ID
- `POST /veiculos` - Adiciona um novo veículo
- `PUT /veiculos` - Atualiza um veículo existente
- `DELETE /veiculos` - Remove um veículo pelo ID

### Empréstimos
- `GET /emprestimos` - Lista todos os empréstimos
- `GET /emprestimo` - Busca um empréstimo pelo ID
- `POST /emprestimos` - Registra um novo empréstimo
- `PUT /emprestimos` - Atualiza um empréstimo existente
- `DELETE /emprestimos` - Remove um empréstimo pelo ID

# Caso de Uso 1: Cadastro de Cliente
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Cadastrar um novo cliente no sistema.  
**Pré-condições:** O usuário tem as informações necessárias do cliente (nome, endereço, idade, CPF).

### Caminho Principal:
1. O usuário acessa o endpoint `POST /clientes`.
2. O sistema recebe os dados: nome, endereço, idade e CPF.
3. O sistema valida o CPF (para garantir unicidade e formato correto).
4. O cliente é inserido no banco de dados.
5. O sistema retorna uma confirmação de sucesso.

**Pós-condição:** O cliente é adicionado com sucesso e está disponível para visualização em `GET /clientes`.

---

# Caso de Uso 2: Consulta de Clientes
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Obter uma lista de todos os clientes cadastrados.  
**Pré-condições:** O sistema possui clientes cadastrados.

### Caminho Principal:
1. O usuário acessa o endpoint `GET /clientes`.
2. O sistema recupera a lista de todos os clientes do banco de dados.
3. O sistema retorna um array JSON com as informações dos clientes.

**Pós-condição:** O usuário visualiza a lista de todos os clientes cadastrados.

---

# Caso de Uso 3: Atualização de Cliente
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Atualizar as informações de um cliente existente.  
**Pré-condições:** O cliente existe e o usuário tem o ID do cliente.

### Caminho Principal:
1. O usuário acessa o endpoint `PUT /cliente`.
2. O sistema recebe o ID do cliente e as novas informações (nome, endereço, idade, CPF).
3. O sistema valida as novas informações e atualiza o registro no banco de dados.
4. O sistema retorna uma confirmação de sucesso.

**Pós-condição:** As informações do cliente são atualizadas no banco de dados.

---

# Caso de Uso 4: Cadastro de Veículo
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Cadastrar um novo veículo no sistema.  
**Pré-condições:** O usuário tem as informações necessárias do veículo (modelo, marca, ano de fabricação, valor do empréstimo, placa, disponibilidade).

### Caminho Principal:
1. O usuário acessa o endpoint `POST /veiculos`.
2. O sistema recebe os dados: modelo, marca, ano de fabricação, valor do empréstimo, placa e disponibilidade.
3. O sistema valida a placa (para garantir unicidade e formato correto).
4. O veículo é inserido no banco de dados.
5. O sistema retorna uma confirmação de sucesso.

**Pós-condição:** O veículo é adicionado com sucesso e está disponível para visualização em `GET /veiculos`.

---

# Caso de Uso 5: Realização de Empréstimo
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Registrar um novo empréstimo de um veículo.  
**Pré-condições:** Um cliente e um veículo já estão cadastrados no sistema e o veículo está disponível.

### Caminho Principal:
1. O usuário acessa o endpoint `POST /emprestimos`.
2. O sistema recebe os dados: ID do cliente, ID do veículo, data de início do empréstimo, data de devolução e valor do empréstimo.
3. O sistema valida a disponibilidade do veículo.
4. O sistema insere o empréstimo no banco de dados e marca o veículo como indisponível.
5. O sistema retorna uma confirmação de sucesso.

**Pós-condição:** O empréstimo é registrado e o veículo é marcado como não disponível.

---

# Caso de Uso 6: Consulta de Empréstimos
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Visualizar os empréstimos ativos ou históricos de veículos.  
**Pré-condições:** Existem empréstimos cadastrados no sistema.

### Caminho Principal:
1. O usuário acessa o endpoint `GET /emprestimos`.
2. O sistema recupera a lista de todos os empréstimos no banco de dados.
3. O sistema retorna um array JSON com as informações dos empréstimos.

**Pós-condição:** O usuário visualiza os empréstimos existentes.

---

# Caso de Uso 7: Devolução de Veículo
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Registrar a devolução de um veículo emprestado.  
**Pré-condições:** O empréstimo já está registrado e o veículo está indisponível.

### Caminho Principal:
1. O usuário acessa o endpoint `PUT /emprestimos`.
2. O sistema recebe o ID do empréstimo e a data de devolução.
3. O sistema atualiza o registro do empréstimo com a data de devolução e marca o veículo como disponível novamente.
4. O sistema retorna uma confirmação de sucesso.

**Pós-condição:** O veículo é marcado como disponível no banco de dados.

---

# Caso de Uso 8: Remoção de Cliente
**Ator:** Usuário (Administrador/Sistema)  
**Objetivo:** Remover um cliente do sistema.  
**Pré-condições:** O cliente existe no sistema e não está associado a empréstimos ativos.

### Caminho Principal:
1. O usuário acessa o endpoint `DELETE /cliente`.
2. O sistema recebe o ID do cliente.
3. O sistema verifica se o cliente não tem empréstimos pendentes.
4. O sistema remove o cliente do banco de dados.
5. O sistema retorna uma confirmação de sucesso.

**Pós-condição:** O cliente é removido do banco de dados.




