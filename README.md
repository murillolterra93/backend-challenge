# JWT Validator API com Testes Automatizados

Este projeto expõe uma API que valida tokens JWT conforme regras específicas. Além disso, há um conjunto de testes automatizados implementados com Cypress para garantir a validade e o comportamento da aplicação.

## Sumário

- [Descrição do Projeto](#descrição-do-projeto)
- [Funcionalidades](#funcionalidades)
- [Requisitos de Sistema](#requisitos-de-sistema)
- [Instalação](#instalação)
- [Executando o Servidor](#executando-o-servidor)
- [Executando os Testes](#executando-os-testes)
- [Detalhes Técnicos](#detalhes-técnicos)
- [Estrutura de Diretórios](#estrutura-de-diretórios)
- [Contribuição](#contribuição)
- [Licença](#licença)

## Descrição do Projeto

Esta aplicação valida tokens JWT conforme as seguintes regras:

- O JWT deve ser válido.
- Deve conter exatamente 3 claims: `Name`, `Role`, e `Seed`.
- O claim `Name` não pode conter números e seu tamanho máximo é de 256 caracteres.
- O claim `Role` deve conter um dos seguintes valores: `Admin`, `Member` ou `External`.
- O claim `Seed` deve ser um número primo.

## Funcionalidades

- **API REST** para validação de JWT.
- **Validação automática** de claims conforme as regras descritas.
- **Testes automatizados** utilizando Cypress para garantir a robustez e consistência da API.

## Requisitos de Sistema

- [Node.js](https://nodejs.org/) (versão 12 ou superior)
- [npm](https://www.npmjs.com/) ou [yarn](https://yarnpkg.com/)
- [Cypress](https://www.cypress.io/)

## Instalação

### Passo 1: Clonar o Repositório

Clone este repositório em sua máquina local:

git clone https://github.com/SEU_USUARIO/jwt-validator.git
cd jwt-validator


### Passo 2: Instalar Dependências
Instale todas as dependências necessárias para o projeto:


npm install
Passo 3: Instalar o Cypress

### Instale o Cypress para os testes automatizados:
npm install cypress --save-dev


### Executando o Servidor
Rodando o Servidor com Node.js
Você pode rodar o servidor normalmente usando o Node.js:
npm start

### Rodando o Servidor com Nodemon (Desenvolvimento)
Para facilitar o desenvolvimento, use o nodemon, que reinicia o servidor automaticamente ao detectar mudanças no código:
npm run dev
O servidor será iniciado e estará disponível em http://localhost:3000.

### Executando os Testes
Rodando os Testes com Cypress
Para rodar os testes no modo "headless" (sem abrir o navegador), execute o seguinte comando:
bash
Copiar código
npx cypress run
Para rodar os testes em modo interativo (com interface gráfica), execute:
bash
Copiar código
npx cypress open
Isso abrirá o painel do Cypress, onde você pode executar os testes manualmente e visualizar os resultados.

## Detalhes Técnicos
### 1. Validação do JWT
A API expõe um endpoint POST /validate-jwt que recebe um JSON contendo um JWT. A lógica de validação segue estas etapas:

Verifica se o JWT é válido.
Verifica se o JWT contém apenas os claims Name, Role e Seed.
Valida que o claim Name não contém números e que não excede 256 caracteres.
Valida que o claim Role é um dos valores permitidos: Admin, Member ou External.
Valida que o claim Seed é um número primo.

#### 2. Testes Automatizados
Os testes verificam os seguintes casos:

Validação de JWTs válidos: Testes verificam JWTs que seguem todas as regras.
Validação de JWTs inválidos: Testes cobrem casos como claims adicionais, Name contendo números, Seed não sendo primo, entre outros.
Cobertura de Erros: Testes verificam as respostas de erro da API quando são fornecidos JWTs malformados.

### 3. Estrutura de Rotas
A API possui uma única rota:

POST /validate-jwt: Valida o JWT com base nas regras especificadas.
Exemplo de requisição:

POST /validate-jwt
Content-Type: application/json

{
  "token": "eyJhbGciOiJIUzI1NiJ9.eyJSb2xlIjoiQWRtaW4iLCJTZWVkIjoiNzUxIiwiTmFtZSI6IkFsaWNlIE5ldXRvbiJ9.H5g3lz0xW6ZVKl8ctZoxb_bTcCnAguqfHl5wx1uGVHs"
}

### Estrutura de Diretórios
jwt-validator/
│
├── cypress/                # Testes automatizados com Cypress
│   └── integration/
│       └── jwtValidator.spec.js
│
├── node_modules/           # Dependências instaladas
├── src/
│   └── server.js           # Código do servidor Node.js com Express
│
├── .gitignore              # Arquivos ignorados pelo Git
├── package.json            # Arquivo de configuração do npm
├── README.md               # Documentação do projeto
└── cypress.json            # Configuração do Cypress
