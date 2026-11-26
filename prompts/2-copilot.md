*primeiro prompt principal*


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

*segundo prompt principal*

Quero que você faça uma VALIDAÇÃO GERAL E COMPLETA deste projeto de lista de tarefas.

IMPORTANTE: não quero apenas que você analise o código visualmente. Quero que você realmente execute e teste o projeto sempre que possível.

## OBJETIVO

Garantir que o sistema esteja funcionando de ponta a ponta, verificando:

- Backend
- Frontend
- Banco de dados
- API
- Integração Frontend ↔ Backend
- CRUD completo de tarefas
- Tratamento de erros
- Rotas
- Requisições HTTP
- Estados da interface
- Configurações e variáveis de ambiente
- Scripts do package.json
- Possíveis erros de execução
- Possíveis problemas que só aparecem durante o uso real

O backend e o frontend já foram executados separadamente e aparentemente funcionaram, mas quero uma validação mais rigorosa de todo o sistema.

## REGRA PRINCIPAL

Antes de alterar qualquer código:

1. Analise toda a estrutura do projeto.
2. Identifique onde estão o frontend e o backend.
3. Identifique a tecnologia utilizada em cada parte.
4. Analise os package.json.
5. Analise as rotas da API.
6. Analise os controllers, services, models e demais camadas existentes.
7. Analise como o frontend consome a API.
8. Identifique como o banco de dados está configurado.
9. Identifique as variáveis de ambiente necessárias.
10. Entenda o fluxo completo de criação, leitura, atualização e exclusão de tarefas.

Não faça alterações simplesmente porque você acha que algo poderia ser melhor. Primeiro identifique problemas reais.

---

# 1. TESTE DO BACKEND

Execute o backend e verifique se ele inicia corretamente.

Verifique:

- npm install / dependências
- scripts do package.json
- inicialização do servidor
- porta utilizada
- conexão com banco de dados
- variáveis de ambiente
- migrations, se existirem
- models
- controllers
- services
- middlewares
- tratamento de erros
- rotas
- status HTTP retornados
- formato dos JSON retornados

Se houver algum erro de inicialização, descubra a causa e corrija.

---

# 2. TESTE COMPLETO DO CRUD

Faça testes reais da API.

Você pode utilizar Postman, Thunder Client, curl ou outra ferramenta equivalente disponível no ambiente.

Teste TODOS os endpoints relacionados às tarefas.

O CRUD precisa ser validado individualmente:

### CREATE

Criar uma nova tarefa.

Verificar:

- endpoint
- método HTTP
- body
- validação dos dados
- persistência no banco
- resposta HTTP
- JSON retornado
- ID gerado

Depois confirme que a tarefa realmente foi salva.

### READ

Buscar todas as tarefas.

Verificar:

- endpoint
- método HTTP
- resposta
- estrutura do JSON
- dados retornados
- conexão com banco

Depois busque uma tarefa específica por ID, caso exista essa rota.

### UPDATE

Atualizar uma tarefa existente.

Verificar:

- endpoint
- método HTTP
- body
- validação
- atualização no banco
- resposta HTTP

Depois faça uma nova consulta para confirmar que a alteração realmente foi persistida.

### DELETE

Excluir uma tarefa existente.

Verificar:

- endpoint
- método HTTP
- resposta HTTP

Depois tente buscar novamente a tarefa excluída para confirmar que ela realmente não existe mais.

---

# 3. TESTES DE ERRO

Não teste somente o caminho feliz.

Teste também situações como:

- criar tarefa sem campos obrigatórios
- enviar campos com tipos incorretos
- enviar ID inexistente
- atualizar tarefa inexistente
- excluir tarefa inexistente
- enviar JSON inválido, se aplicável
- acessar rota inexistente
- utilizar método HTTP incorreto

Verifique se o backend retorna erros apropriados e não simplesmente quebra.

---

# 4. BANCO DE DADOS

Verifique se os dados realmente estão sendo persistidos.

Faça o seguinte fluxo:

1. Criar tarefa pela API.
2. Confirmar resposta.
3. Consultar a tarefa.
4. Atualizar a tarefa.
5. Consultar novamente.
6. Excluir a tarefa.
7. Confirmar que foi excluída.

Quero ter certeza de que não existe apenas um armazenamento temporário no frontend.

---

# 5. TESTE DO FRONTEND

Execute o frontend.

Verifique:

- npm install
- npm run dev/build ou script equivalente
- erros no terminal
- erros no console do navegador
- carregamento da aplicação
- componentes
- páginas
- formulários
- botões
- estados de loading
- mensagens de erro
- mensagens de sucesso
- atualização da lista

Teste a aplicação como um usuário real.

---

# 6. TESTE DA INTEGRAÇÃO FRONTEND + BACKEND

Essa é uma das partes mais importantes.

Não quero apenas que frontend e backend funcionem separadamente.

Verifique se eles realmente conseguem conversar entre si.

Teste pelo frontend:

1. Criar uma tarefa.
2. Verificar se aparece na lista.
3. Atualizar a tarefa.
4. Verificar se a alteração aparece na interface.
5. Excluir a tarefa.
6. Verificar se desaparece da interface.
7. Recarregar a página.
8. Confirmar que os dados continuam corretos.

Verifique também:

- URL da API
- portas
- CORS
- headers
- métodos HTTP
- body das requisições
- tratamento das respostas
- tratamento de erros
- estados de loading
- sincronização da interface com o backend

---

# 7. TESTE DE PONTA A PONTA

Faça pelo menos um fluxo completo simulando um usuário real:

ABRIR SISTEMA
→ carregar tarefas
→ criar tarefa
→ visualizar tarefa
→ editar tarefa
→ salvar alteração
→ visualizar alteração
→ excluir tarefa
→ confirmar exclusão
→ recarregar página
→ confirmar estado final

Se alguma etapa falhar, investigue a causa.

---

# 8. VERIFICAÇÃO DE CÓDIGO

Depois dos testes, analise se existem:

- imports quebrados
- arquivos não utilizados
- funções que nunca são chamadas
- endpoints inconsistentes
- nomes diferentes entre frontend e backend
- campos diferentes entre model, API e frontend
- erros de tipagem, caso exista TypeScript
- URLs hardcoded incorretas
- variáveis de ambiente ausentes
- dependências faltando
- dependências desnecessárias
- scripts incorretos
- problemas de CORS
- problemas de tratamento de exceções

---

# 9. CORREÇÕES

Se encontrar problemas:

1. Explique o problema.
2. Identifique a causa.
3. Corrija o problema.
4. Execute novamente o teste que falhou.
5. Confirme que a correção funcionou.
6. Verifique se a correção não quebrou outra parte do sistema.

Não faça mudanças desnecessárias na arquitetura ou no design do projeto.

Preserve a estrutura atual sempre que possível.

---

# 10. RELATÓRIO FINAL

Ao terminar, me entregue um relatório organizado contendo:

## STATUS GERAL

Informe uma destas opções:

- APROVADO
- APROVADO COM RESSALVAS
- REPROVADO

## BACKEND

Informe:

- iniciou corretamente?
- banco conectado?
- API funcionando?
- CRUD funcionando?
- problemas encontrados?

## CRUD

Monte uma tabela:

| Operação | Endpoint | Método | Resultado | Status |
|----------|----------|--------|-----------|--------|
| Criar | ... | POST | ... | OK/FALHA |
| Listar | ... | GET | ... | OK/FALHA |
| Buscar | ... | GET | ... | OK/FALHA |
| Atualizar | ... | PUT/PATCH | ... | OK/FALHA |
| Excluir | ... | DELETE | ... | OK/FALHA |

## FRONTEND

Informe:

- iniciou?
- interface carregou?
- criação funciona?
- edição funciona?
- exclusão funciona?
- listagem funciona?
- existem erros no console?

## INTEGRAÇÃO

Informe:

- frontend consegue acessar backend?
- CORS está correto?
- requisições funcionam?
- respostas são tratadas corretamente?

## PROBLEMAS ENCONTRADOS

Liste cada problema encontrado e sua gravidade:

- CRÍTICO
- ALTO
- MÉDIO
- BAIXO

## CORREÇÕES REALIZADAS

Liste exatamente quais arquivos foram modificados e o que foi alterado.

## TESTES REALIZADOS

Liste os testes executados e seus resultados.

## CONCLUSÃO

Diga claramente se você considera que o projeto está realmente funcional e pronto para ser apresentado/entregue.

IMPORTANTE:

Não diga que algo está funcionando apenas porque o código parece correto.

Sempre que possível, EXECUTE, TESTE E CONFIRME.
Se não conseguir executar algum teste, informe explicitamente que ele não pôde ser realizado e explique o motivo.
*terceiro prompt principal*

# PROMPT — CORREÇÃO DAS PENDÊNCIAS DE PRODUÇÃO E LINT

Quero que você resolva os dois problemas identificados na conclusão da validação anterior do meu projeto de lista de tarefas.

**Pendências identificadas:**

1. Problemas relacionados ao preview de produção.
2. Problemas de formatação que estão impedindo a execução correta do lint.

O objetivo é corrigir essas pendências e deixar o projeto preparado para uma entrega, preservando integralmente os recursos que já estão funcionando.

## 1. REGRA PRINCIPAL: PRESERVAR O PROJETO

Antes de realizar qualquer alteração:

- Analise a estrutura atual do projeto.
- Consulte os resultados da validação anterior.
- Identifique a causa real dos dois problemas.
- Verifique quais arquivos precisam ser modificados.
- Não reconstrua o projeto.
- Não altere a arquitetura sem necessidade.
- Não modifique o layout ou o design.
- Não remova funcionalidades existentes.
- Não altere endpoints ou contratos da API sem necessidade comprovada.
- Não modifique configurações que já estejam funcionando sem justificativa técnica.

Faça somente as alterações necessárias para resolver os problemas identificados.

## 2. CORREÇÃO DO PREVIEW DE PRODUÇÃO

Investigue por que o preview de produção não está funcionando corretamente.

Verifique:

- Scripts disponíveis no package.json.
- Configuração do processo de build.
- Dependências necessárias para compilação.
- Variáveis de ambiente utilizadas em produção.
- URL de comunicação entre frontend e backend.
- Configurações de CORS.
- Caminhos e referências aos arquivos gerados.
- Configuração de rotas do frontend.
- Possíveis erros durante a compilação.
- Erros no terminal e no console do navegador.

Execute o processo de produção de acordo com a tecnologia utilizada no projeto.

Não considere suficiente que o frontend funcione apenas com o comando de desenvolvimento.

Quero que você:

1. Execute o build de produção.
2. Identifique e corrija eventuais erros.
3. Execute o preview utilizando o script existente ou o procedimento equivalente.
4. Acesse a aplicação no navegador, quando houver ferramenta disponível.
5. Verifique se as páginas e os recursos carregam corretamente.
6. Teste a comunicação com o backend.
7. Verifique se as funcionalidades principais continuam funcionando.

Caso exista algum problema relacionado às variáveis de ambiente ou à configuração externa, identifique exatamente o que está faltando. Não invente valores ou exponha credenciais.

## 3. CORREÇÃO DO LINT E DA FORMATAÇÃO

Investigue por que a formatação está impedindo a execução do lint.

Verifique:

- Configuração do ESLint.
- Configuração do Prettier, caso exista.
- Scripts de validação no package.json.
- Regras de formatação.
- Imports e declarações.
- Problemas de sintaxe.
- Erros de tipagem, caso exista TypeScript.
- Incompatibilidades entre ferramentas e configurações.

Execute o comando de lint existente e analise os erros apresentados.

Corrija os problemas encontrados nos arquivos correspondentes.

IMPORTANTE:

- Não desative regras do ESLint apenas para fazer o comando passar.
- Não remova verificações de qualidade.
- Não ignore erros utilizando configurações artificiais.
- Não altere indiscriminadamente todos os arquivos.
- Utilize correções automáticas somente quando forem seguras e revise os resultados.
- Preserve o comportamento original das funcionalidades.

Depois das correções, execute novamente o lint e confirme o resultado.

## 4. TESTES DE REGRESSÃO

Após corrigir os dois problemas, verifique se o restante do projeto continua funcionando.

Teste:

**Backend**
- Inicialização do servidor.
- Conexão com PostgreSQL.
- Funcionamento das rotas.
- Respostas da API.

**CRUD**
- Criar tarefas.
- Listar tarefas.
- Consultar tarefas, caso exista essa funcionalidade.
- Atualizar tarefas.
- Excluir tarefas.

**Frontend**
- Inicialização.
- Carregamento das páginas.
- Formulários.
- Botões.
- Listagem de tarefas.
- Edição e exclusão.
- Mensagens de sucesso e erro.

**Integração**
- Comunicação entre frontend e backend.
- Persistência dos dados no PostgreSQL.
- Atualização da interface após as operações.
- Funcionamento após recarregar a página.

Não apague dados existentes do banco durante os testes.

## 5. LIMITES DAS ALTERAÇÕES

Não aproveite essa tarefa para realizar refatorações gerais ou implementar novas funcionalidades.

Não altere o que não estiver diretamente relacionado aos problemas apresentados.

Caso encontre outro problema que não esteja relacionado às duas pendências, registre-o no relatório, mas não faça alterações adicionais sem necessidade.

Se não conseguir resolver alguma pendência por depender de configuração externa, explique claramente o motivo e indique o que precisa ser configurado.

## 6. RELATÓRIO FINAL

Ao concluir, apresente um relatório contendo:

### A. Preview de produção
- Qual era o problema?
- Qual era a causa?
- O que foi alterado?
- O build foi executado com sucesso?
- O preview funcionou?
- A comunicação com o backend foi validada?

### B. Lint e formatação
- Qual era o problema?
- Quais arquivos apresentavam erros?
- O que foi corrigido?
- O comando de lint foi executado novamente?
- O resultado foi aprovado?

### C. Arquivos modificados
Informe os caminhos de todos os arquivos alterados e o motivo de cada alteração.

### D. Testes de regressão
Apresente os testes realizados e seus resultados.

### E. Problemas pendentes
Liste qualquer problema que não tenha sido resolvido, explicando o motivo.

### F. STATUS FINAL

Classifique o resultado como:

- **APROVADO:** os dois problemas foram resolvidos e os testes foram concluídos com sucesso.
- **APROVADO COM RESSALVAS:** houve correções, mas ainda existem pendências.
- **REPROVADO:** existem problemas que impedem considerar o projeto pronto para entrega.

## INSTRUÇÃO FINAL

Trabalhe como um desenvolvedor responsável por estabilizar uma aplicação já funcional.

Não quero que você simplesmente faça os comandos passarem. Quero que identifique as causas, corrija os problemas e comprove os resultados por meio de testes reais.

**Corrija as duas pendências, preserve todas as funcionalidades existentes e não declare sucesso sem comprovação.**

*quarto prompt principal*

# OBJETIVO: AUDITORIA E CORREÇÃO DE VULNERABILIDADES NAS DEPENDÊNCIAS

Quero que você realize uma auditoria de segurança completa nas dependências do meu projeto de lista de tarefas.

Na última instalação das dependências, foram identificados 22 avisos de auditoria:

- 12 vulnerabilidades moderadas.
- 10 vulnerabilidades altas.

Sua missão é investigar essas vulnerabilidades, corrigir as que puderem ser resolvidas com segurança e preservar todas as funcionalidades existentes.

## 1. ANÁLISE INICIAL

Antes de modificar qualquer arquivo:

1. Analise os package.json do frontend e do backend.
2. Identifique os gerenciadores de pacotes utilizados em cada parte.
3. Analise os respectivos arquivos de lock.
4. Execute a auditoria de segurança das dependências.
5. Identifique todas as vulnerabilidades encontradas.
6. Identifique quais dependências estão envolvidas.
7. Descubra se são dependências diretas ou transitivas.
8. Verifique se afetam o ambiente de produção ou somente o desenvolvimento.
9. Identifique quais possuem atualizações disponíveis.

Não faça atualizações antes de entender os resultados.

## 2. PRIORIZAÇÃO DAS VULNERABILIDADES

Classifique os problemas encontrados:

- CRÍTICO
- ALTO
- MODERADO
- BAIXO

Para cada vulnerabilidade, informe:

- Nome da dependência.
- Versão instalada.
- Versão corrigida disponível, caso exista.
- Gravidade.
- Tipo de vulnerabilidade.
- Dependência que introduziu o pacote vulnerável.
- Se existe risco para a aplicação em produção.
- Se a atualização pode causar incompatibilidade.

Diferencie vulnerabilidades reais de avisos que não representam risco direto para o funcionamento da aplicação.

## 3. CORREÇÃO CONTROLADA

Corrija as vulnerabilidades utilizando versões seguras e compatíveis com o projeto.

REGRAS IMPORTANTES:

- Preserve as versões compatíveis com a arquitetura atual.
- Não atualize todas as dependências indiscriminadamente.
- Não utilize `npm audit fix --force`.
- Não force atualizações principais (major) sem necessidade comprovada.
- Não remova bibliotecas funcionais apenas para zerar o relatório.
- Não desative verificações de segurança.
- Não altere o comportamento da aplicação.
- Não modifique dependências sem relação com as vulnerabilidades identificadas.
- Preserve os arquivos de lock existentes.
- Não crie arquivos de lock concorrentes desnecessariamente.

Antes de atualizar uma dependência, verifique se a nova versão é compatível com as bibliotecas que dependem dela.

Caso uma vulnerabilidade não tenha correção disponível sem mudanças incompatíveis, não faça uma alteração arriscada. Explique a situação e apresente alternativas.

## 4. PRESERVAÇÃO DAS FUNCIONALIDADES

Depois das atualizações, confirme que continuam funcionando:

- Frontend.
- Backend.
- API.
- PostgreSQL.
- CRUD completo.
- Integração entre frontend e backend.
- Preview de produção com Wrangler.
- Configurações existentes.

Não apague dados do banco durante os testes.

## 5. TESTES APÓS AS CORREÇÕES

Execute novamente:

- Instalação das dependências utilizando o gerenciador correto.
- Auditoria de segurança.
- Testes automatizados do frontend.
- Testes automatizados do backend.
- Lint.
- TypeScript.
- Build de produção.
- Preview local.
- Testes de integração.
- Testes do CRUD completo.

Compare os resultados com os testes anteriores.

Se alguma atualização causar uma falha, investigue e corrija sem comprometer as funcionalidades existentes.

## 6. RELATÓRIO FINAL

Apresente um relatório contendo:

### A. Vulnerabilidades encontradas
Liste as dependências, versões e gravidades.

### B. Correções realizadas
Informe quais dependências foram atualizadas e quais arquivos foram modificados.

### C. Vulnerabilidades restantes
Explique quais não puderam ser corrigidas e por quê.

### D. Testes realizados
Apresente os resultados dos testes após as atualizações.

### E. Impacto no projeto
Informe se alguma funcionalidade foi afetada.

### F. Resultado da auditoria
Classifique como:

- APROVADO: vulnerabilidades corrigidas ou riscos restantes devidamente justificados e aceitos.
- APROVADO COM RESSALVAS: existem vulnerabilidades sem correção segura.
- REPROVADO: existem vulnerabilidades importantes sem tratamento adequado ou falhas introduzidas pelas atualizações.

## INSTRUÇÃO FINAL

Atue como um desenvolvedor responsável pela segurança de uma aplicação existente.

Não quero simplesmente zerar os avisos do npm audit. Quero reduzir os riscos reais sem comprometer a estabilidade do projeto.

**Segurança em primeiro lugar, mas sem quebrar funcionalidades que já estão prontas.**

*quinto prompt principal*

