# Sistema de Gerenciamento de Empréstimos

Este projeto é um sistema básico para gerenciamento de empréstimos de itens, oferecendo funcionalidades como cadastro de usuários, cadastro de veículos (itens de empréstimo) e gerenciamento dos empréstimos, incluindo a devolução e valores dos empréstimos.

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

## Estrutura do Projeto

```bash
├── controllers
│   ├── clientes.js   # Controlador de clientes (CRUD)
│   ├── veiculos.js   # Controlador de veículos (CRUD)
│   └── emprestimos.js # Controlador de empréstimos (CRUD)
├── routes.js         # Definição das rotas da API
├── createTable.js    # Script para criação e inicialização do banco de dados
├── db.js             # Conexão com o banco de dados SQLite
├── server.js         # Arquivo principal que inicializa o servidor
└── backend/SSL       # Certificados SSL para HTTPS

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
