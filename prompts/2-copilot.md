# Contexto do projeto

Estou desenvolvendo uma aplicação de lista de tarefas para uma avaliação do SENAC.

O projeto possui duas partes:

- **Back-end:** API REST desenvolvida em Node.js;
- **Front-end:** interface da aplicação.

Preciso que você trabalhe respeitando a estrutura e os caminhos abaixo.

---

# Caminhos do projeto

## Back-end

```text
C:\Users\arthur62382536\OneDrive - SENAC-SC\Documentos\AvaliaçãoRenan\AvaliacaoFinalNodeAPI
```

Este é o diretório principal do back-end.

## Front-end

```text
C:\Users\arthur62382536\documents\especifica-es-em-a-o
```

Este é o diretório principal do front-end.

**Importante:** não misture os arquivos do front-end com os arquivos do back-end. Cada projeto deve permanecer em seu respectivo diretório.

---

# Tecnologias obrigatórias do back-end

Utilize:

- Node.js;
- Express;
- Sequelize;
- PostgreSQL (PG);
- NVM para gerenciamento da versão do Node.js;
- npm.

A aplicação deve ser desenvolvida utilizando JavaScript.

---

# Estrutura obrigatória do back-end

Organize o projeto seguindo uma arquitetura separada por responsabilidades.

A estrutura esperada é:

```text
AvaliacaoFinalNodeAPI/
│
├── src/
│   ├── controller/
│   ├── model/
│   ├── router/
│   └── service/
│
├── index.html
├── server.js
├── package.json
├── package-lock.json
├── .gitignore
└── ...
```

### Responsabilidade das pastas

#### `src/controller`

Responsável por receber as requisições HTTP, chamar os serviços necessários e retornar as respostas para o cliente.

#### `src/model`

Responsável pelos modelos do Sequelize e pela definição das entidades utilizadas pela aplicação.

#### `src/service`

Responsável pelas regras de negócio da aplicação.

Não colocar regras de negócio complexas diretamente nos controllers.

#### `src/router`

Responsável pela definição das rotas da API e pelo direcionamento das requisições para os controllers.

---

# Arquivos principais

## `server.js`

Responsável por inicializar o servidor Express, configurar os middlewares necessários e iniciar a aplicação.

Utilizar Express corretamente.

O servidor deve utilizar uma porta configurável por variável de ambiente, utilizando uma porta padrão caso ela não esteja definida.

---

## `index.html`

Manter somente se for necessário para a estrutura atual do projeto.

Não transformar o back-end em uma aplicação front-end.

O front-end principal continuará no diretório separado:

```text
C:\Users\arthur62382536\documents\especifica-es-em-a-o
```

---

# Banco de dados

Utilizar:

- PostgreSQL;
- Sequelize;
- pacote `pg`.

O Sequelize deve ser utilizado para comunicação entre a API e o PostgreSQL.

Não realizar consultas SQL diretamente quando o Sequelize puder executar a operação.

Criar uma configuração organizada para a conexão com o banco.

As informações sensíveis de conexão devem utilizar variáveis de ambiente.

Não colocar senhas ou credenciais diretamente no código.

---

# CRUD de tarefas

A API deve possuir um CRUD completo para tarefas.

Implementar as operações:

### CREATE

Criar uma nova tarefa.

A tarefa deve possuir, no mínimo:

- ID;
- título;
- data de conclusão;
- status.

---

### READ

Permitir:

- Buscar todas as tarefas;
- Buscar uma tarefa específica pelo ID.

---

### UPDATE

Permitir alterar os dados de uma tarefa existente.

Deve ser possível alterar:

- título;
- data;
- status.

---

### DELETE

Permitir excluir uma tarefa pelo ID.

---

# Rotas

Criar rotas REST organizadas para o CRUD de tarefas.

Exemplo de estrutura:

```text
GET    /tasks
GET    /tasks/:id
POST   /tasks
PUT    /tasks/:id
DELETE /tasks/:id
```

Utilizar os métodos HTTP corretamente.

As rotas devem chamar os respectivos controllers.

Os controllers devem utilizar os services.

Os services devem utilizar os models/Sequelize.

Fluxo esperado:

```text
Request
   ↓
Router
   ↓
Controller
   ↓
Service
   ↓
Model / Sequelize
   ↓
PostgreSQL
```

---

# HTTP e respostas

Utilizar corretamente os códigos HTTP.

Exemplos:

### Sucesso

- `200 OK` — consulta ou atualização realizada com sucesso;
- `201 Created` — recurso criado com sucesso;
- `204 No Content` — exclusão realizada com sucesso, quando apropriado.

### Erros do cliente

- `400 Bad Request` — dados inválidos;
- `404 Not Found` — recurso não encontrado;
- `409 Conflict` — conflito de dados, quando aplicável.

### Erros internos

- `500 Internal Server Error` — erro inesperado no servidor.

As respostas da API devem possuir uma estrutura consistente em JSON.

---

# Tratamento de erros

Implementar tratamento de erros de forma organizada.

Não deixar erros internos do Node.js ou Sequelize quebrarem a aplicação sem tratamento.

Criar um padrão consistente para respostas de erro.

Exemplo:

```json
{
  "error": true,
  "message": "Tarefa não encontrada."
}
```

Evitar expor informações sensíveis ou detalhes internos do banco de dados ao cliente.

---

# NVM e ambiente Node.js

O projeto deve funcionar utilizando uma versão estável e compatível do Node.js.

Antes de alterar versões ou configurações do ambiente, verificar a versão atual do Node.js e do npm.

Não instalar versões aleatórias ou incompatíveis.

Se houver problema relacionado ao NVM, Node.js ou npm, identificar primeiro a causa antes de modificar o ambiente.

Comandos úteis para verificar o ambiente:

```bash
node -v
npm -v
nvm version
```

---

# Scripts do package.json

Configurar o projeto para que a aplicação possa ser iniciada em modo de desenvolvimento utilizando:

```bash
npm run dev
```

O `package.json` deve possuir um script `dev` apropriado.

Utilizar uma ferramenta adequada para reinicialização automática durante o desenvolvimento, como `nodemon`, se necessário.

Exemplo esperado:

```json
"scripts": {
  "dev": "nodemon server.js"
}
```

Não assumir que esse script já existe. Caso não exista, configure-o corretamente.

---

# Dependências

Utilizar as dependências necessárias para o projeto, principalmente:

```bash
npm install express sequelize pg
```

Para desenvolvimento, utilizar uma ferramenta como:

```bash
npm install -D nodemon
```

Não adicionar bibliotecas desnecessárias.

Antes de instalar uma dependência nova, verificar se ela realmente é necessária.

---

# Variáveis de ambiente

Utilizar `.env` para informações de configuração que não devem ficar diretamente no código.

Exemplos de informações que podem ficar no `.env`:

```text
PORT=
DB_HOST=
DB_PORT=
DB_NAME=
DB_USER=
DB_PASSWORD=
```

Adicionar o `.env` ao `.gitignore`.

Criar, se necessário, um `.env.example` contendo somente os nomes das variáveis, sem credenciais reais.

---

# .gitignore

Criar ou manter um `.gitignore` adequado para Node.js.

Ele deve ignorar pelo menos:

```text
node_modules/
.env
```

Também ignorar arquivos temporários e arquivos gerados que não devem ser versionados.

Não ignorar:

```text
package.json
package-lock.json
src/
server.js
```

---

# Organização e qualidade do código

O código deve ser:

- Simples;
- Organizado;
- Legível;
- Adequado para um projeto de avaliação;
- Fácil de explicar para um professor;
- Separado por responsabilidades.

Evitar:

- Código duplicado;
- Controllers gigantes;
- Regras de negócio dentro das rotas;
- Consultas ao banco diretamente dentro das rotas;
- Variáveis de ambiente expostas;
- Dependências desnecessárias;
- Arquivos sem função clara.

Não adicionar arquitetura excessivamente complexa que não seja necessária para o MVP.

---

# Integração com o front-end

O front-end está localizado em:

```text
C:\Users\arthur62382536\documents\especifica-es-em-a-o
```

O back-end deve disponibilizar a API REST para que o front-end possa futuramente consumir as tarefas.

**Não mover o front-end para dentro do back-end.**

Neste momento, priorize a implementação correta da API e sua estrutura.

---

# Ordem de execução

Antes de modificar os arquivos:

1. Verifique a estrutura atual do projeto;
2. Verifique o `package.json`;
3. Verifique a versão do Node.js e npm;
4. Verifique se o Sequelize e PostgreSQL já estão configurados;
5. Identifique o que já existe;
6. Reutilize o código existente quando estiver correto;
7. Não apague arquivos ou funcionalidades sem necessidade;
8. Só depois implemente ou corrija o que estiver faltando.

---

# Critérios de conclusão

Considere o back-end concluído quando:

- O projeto iniciar com `npm run dev`;
- O Express estiver funcionando corretamente;
- A conexão com PostgreSQL estiver configurada;
- Sequelize estiver funcionando;
- O model de tarefas estiver criado;
- As rotas estiverem separadas;
- Os controllers estiverem separados;
- Os services estiverem separados;
- O CRUD estiver funcionando;
- Os métodos HTTP estiverem corretos;
- Os códigos de status HTTP estiverem adequados;
- Os erros estiverem tratados;
- O `.gitignore` estiver configurado;
- As credenciais estiverem protegidas por `.env`;
- A estrutura `src/controller`, `src/model`, `src/router` e `src/service` estiver sendo utilizada;
- `npm run dev` iniciar a aplicação sem erros.

# Regra importante

**Não invente funcionalidades fora do escopo.**

Antes de criar novos arquivos, dependências ou estruturas, verifique o que já existe no projeto.

Se encontrar um problema, explique brevemente o problema, a causa provável e faça a correção necessária.

Priorize uma implementação **simples, funcional e fácil de apresentar em uma avaliação do SENAC**.