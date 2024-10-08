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
