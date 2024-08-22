<h1 align="center">Estudando NodeJs</h1>

> <h2 align="center">Introdução ao Node.js</h2>
> 
> ### # O que é Node.js?
> Node.js é um ambiente de execução JavaScript no lado do servidor, permitindo que você use JavaScript para construir aplicações que rodam fora do navegador. Baseado no motor V8 do Google Chrome, ele permite a execução rápida e eficiente de código JavaScript no servidor.
> 
> ### # Por que Node.js?
> Node.js é popular por seu alto desempenho, graças ao modelo de E/S não-bloqueante e baseado em eventos, que permite a gestão eficiente de múltiplas conexões simultâneas. Ele também unifica a linguagem usada tanto no frontend quanto no backend, simplificando o desenvolvimento. Além disso, possui um vasto ecossistema de pacotes e uma comunidade ativa que facilita a adição de funcionalidades e suporte.
> 
> ### # História do Node.js
> Node.js foi criado por Ryan Dahl em 2009 para superar as limitações dos servidores web tradicionais, que não gerenciavam bem grandes volumes de conexões simultâneas. A solução foi criar um ambiente de execução com E/S não-bloqueante, o que tornou o Node.js ideal para aplicações escaláveis.
> 
> ### # Node.js vs Navegador
> Apesar de ambos utilizarem JavaScript, o Node.js e o ambiente do navegador têm diferenças fundamentais. O Node.js é usado para operações no servidor, como manipulação de arquivos e redes, enquanto o navegador se concentra na interação com o DOM. No Node.js, o JavaScript tem acesso completo ao sistema, exigindo cuidados adicionais com segurança, enquanto no navegador, o JavaScript é executado em um ambiente seguro.
> 
> ### # Executando Código Node.js
> Para executar código no Node.js, você precisa primeiro instalá-lo em seu sistema. Após a instalação, você pode criar um arquivo JavaScript, por exemplo `app.js`, e escrever o código que deseja executar:
>```javascript
> console.log("Hello, Node.js!");
> ```
> 
> Depois, no terminal, você pode executar esse código usando o comando:
> ```bash
> node app.js
> ```
> Isso irá executar o código dentro do arquivo `app.js` e exibir "Hello, Node.js!" no terminal.
> 
> Se você quiser criar um servidor web simples, poderia escrever algo assim:
> ```javascript
> const http = require('http');
> 
> const server = http.createServer((req, res) => {
>   res.statusCode = 200;
>   res.setHeader('Content-Type', 'text/plain');
>   res.end('Hello, World!\n');
> });
> 
> server.listen(3000, () => {
>   console.log('Server running at http://localhost:3000/');
> });
> ```
> E ao rodar `node app.js`, você terá um servidor rodando localmente, que responde com "Hello, World!" para qualquer requisição.

<br>

> <h2 align="center">Introdução aos Módulos no Node.js</h2>
> O Node.js é uma plataforma popular para desenvolver aplicações no lado do servidor. Uma das suas principais características é o suporte a módulos, que permitem dividir o código em partes reutilizáveis, organizadas e de fácil manutenção. No Node.js, existem dois sistemas principais de módulos: **CommonJS** e **ESM (ECMAScript Modules)**. Além disso, você pode criar e importar módulos personalizados, bem como utilizar a palavra-chave `global` para definir variáveis globais.
>
> ### # CommonJS
> O sistema de módulos CommonJS foi o primeiro a ser implementado no Node.js. Ele é amplamente utilizado e tem uma sintaxe simples para exportar e importar módulos.
> - **Exportando Módulos**: Usamos `module.exports` ou `exports` para exportar funções, objetos, ou valores.
> - **Importando Módulos**: Usamos `require` para importar um módulo.
> #### **Exemplo de Módulo CommonJS:**
> ```javascript
> // Nome do arquivo: math.js
> function somar(a, b) {
>     return a + b;
> }
> 
> function subtrair(a, b) {
>     return a - b;
> }
> 
> // Exportando as funções
> module.exports = {
>     somar,
>     subtrair
> };
> ```
> #### **Exemplo de Importação no CommonJS:**
> ```javascript
> // Nome do arquivo: app.js
>
> // Aqui estamos puxando o arquivo 'math.js' para dentro do 'app.js'
> const math = require('./math');
> 
> console.log(math.somar(2, 3)); // Saída: 5
> console.log(math.subtrair(5, 3)); // Saída: 2
> ```
> 
> ### # ESM (ECMAScript Modules)
> O ESM é o sistema de módulos padrão definido na especificação ECMAScript (ES6+). Ele é mais moderno e também é compatível com os navegadores, o que torna o código mais consistente entre o frontend e o backend.
> - **Exportando Módulos**: Usamos `export` para exportar funções, objetos ou valores.
> - **Importando Módulos**: Usamos `import` para importar módulos.
> #### **Exemplo de Módulo ESM:**
> ```javascript
> // math.mjs
> export function somar(a, b) {
>     return a + b;
> }
> 
> export function subtrair(a, b) {
>     return a - b;
> }
> ```
> #### **Exemplo de Importação no ESM:**
> ```javascript
> // app.mjs
> import { somar, subtrair } from './math.mjs';
> 
> console.log(somar(2, 3)); // Saída: 5
> console.log(subtrair(5, 3)); // Saída: 2
> ```
> 
> ### # **Diferenças Principais entre CommonJS e ESM:**
> 1. **Sintaxe**: CommonJS usa `require` e `module.exports`, enquanto ESM usa `import` e `export`.
> 2. **Suporte Nativo**: CommonJS é o sistema de módulos padrão no Node.js, enquanto o ESM foi adicionado em versões mais recentes e requer o uso da extensão `.mjs` ou a definição de `"type": "module"` no `package.json`.
> 3. **Assincronismo**: ESM suporta importações assíncronas, o que permite carregar módulos de maneira mais eficiente.
>
> ### # Módulos Personalizados: Criação e Importação
> Os módulos personalizados são simplesmente arquivos JavaScript que exportam funções, objetos ou valores que podem ser reutilizados em outras partes do seu código.
> #### **Criando um Módulo Personalizado (CommonJS):**
> ```javascript
> // utils.js
> function apresentar(nome) {
>     return `Olá, ${nome}!`;
> }
>
> module.exports = apresentar;
> ```
> **Importando e Usando o Módulo Personalizado:**
> ```javascript
> // app.js
> const apresentar = require('./utils');
>
> console.log(apresentar('Henrique')); // Saída: Olá, Henrique!
> ```
>
> **Criando um Módulo Personalizado (ESM):**
> ```javascript
> // utils.mjs
> export function apresentar(nome) {
>     return `Olá, ${nome}!`;
> }
> ```
> **Importando e Usando o Módulo Personalizado:**
> ```javascript
> // app.mjs
> import { apresentar } from './utils.mjs';
>
> console.log(apresentar('Rick')); // Saída: Olá, Rick!
> ```
>
> ### # Palavara-Chave `global`
> No Node.js, `global` é um objeto especial que pode ser usado para definir variáveis ou funções que estão disponíveis globalmente em toda a aplicação, semelhante ao objeto `window` no navegador.
> #### **Exemplo de Uso do `global`:**
> ```javascript
> // Definindo uma variável global
> global.minhaVarGlobal = 'Este é um valor global';
> 
> console.log(global.minhaVarGlobal); // Saída: Este é um valor global
>
> // Definindo uma função global
> global.apresentar = function(nome) {
>     return `Olá, ${nome}!`;
> };
> 
> console.log(global.apresentar('Node.js')); // Saída: Olá, Node.js!
> ```
>
> #### **Cuidados ao Usar `global`:**
> 1. **Evitar Conflitos**: Como as variáveis e funções no objeto `global` são acessíveis em toda a aplicação, isso pode causar conflitos de nome e tornar o código mais difícil de depurar.
> 2. **Boa Prática**: É uma boa prática evitar o uso de `global` e preferir passar variáveis e funções explicitamente como argumentos ou importá-las de módulos específicos.
>> ###### Você pode aprender mais sobre no artigo: [MDN - Modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)

<br>

> <h2 align="center">Introdução ao NPM</h2>
> O NPM (Node Package Manager) é a ferramenta padrão para gerenciar pacotes no ecossistema Node.js. Ele permite que você instale, compartilhe e gerencie dependências (bibliotecas e ferramentas) que seu projeto precisa. Além disso, o NPM facilita a criação de scripts para automatizar tarefas e suporta a criação e publicação de pacotes. Neste guia, exploraremos detalhadamente os conceitos de npx, Versionamento Semântico, instalações globais e locais, atualização de pacotes, execução de scripts, workspaces e a criação de pacotes.
>
> ### # npx
> O `npx` é uma ferramenta que vem com o NPM e permite executar pacotes diretamente da linha de comando sem instalá-los globalmente no seu sistema. É útil para testar pacotes ou executar comandos únicos.
> #### **Exemplo de Uso do npx:**
> ```bash
> # Usando npx para criar um novo projeto React
> npx create-react-app meu-projeto
> ```
> #### **Explicação:**
> - `npx` baixa e executa o pacote `create-react-app` temporariamente.
> - O comando cria um novo diretório chamado `meu-projeto` com uma aplicação React configurada.
> - **Sem necessidade de instalação global**: O `create-react-app` não precisa ser instalado globalmente, economizando espaço e evitando conflitos com outras versões.
> #### **Vantagens do npx:**
> - **Executa pacotes temporariamente**: Ideal para usar ferramentas sem poluir o ambiente global.
> - **Versão mais recente**: Sempre usa a versão mais atual do pacote.
>
> ### # Versionamento Semântico (Semantic Versioning)
> O Versionamento Semântico (SemVer) é um sistema para versionar pacotes, composto por três números: `MAJOR.MINOR.PATCH`.
> #### **Exemplo de Versionamento Semântico:**
> ```json
> "dependencies": {
>   "express": "^4.17.1"
> }
> ```
> **Explicação:**
> - **`4` (MAJOR)**: Mudanças que quebram a compatibilidade. Atualizações que podem exigir alterações no seu código.
> - **`17` (MINOR)**: Novas funcionalidades que são compatíveis com versões anteriores. Adições que não quebram a compatibilidade.
> - **`1` (PATCH)**: Correções de bugs que não afetam a compatibilidade. Atualizações que apenas resolvem problemas sem introduzir novas funcionalidades.
> #### **Regras de Atualização:**
> - `^4.17.1` permite atualizações para `4.18.0` ou `4.17.2`, mas não para `5.0.0`.
> - `~4.17.1` permite atualizações para `4.17.2`, mas não para `4.18.0`.
> #### **Importância do SemVer:**
> - **Controle de Compatibilidade**: Garante que as atualizações de dependências não quebrem seu código.
> - **Gestão de Dependências**: Ajuda a escolher quando adotar novas funcionalidades ou aplicar correções de bugs.
>
> ### # Instalação Global vs Local
> Você pode instalar pacotes no nível do projeto (local) ou no nível do sistema (global).
>
>  **Instalação Local**: O pacote é instalado no diretório `node_modules` do seu projeto. Usado para dependências específicas do projeto.
>   ```bash
>   # Instalando o pacote 'lodash' localmente
>   npm install lodash
>   ```
>
>  **Explicação:**
>  - O pacote `lodash` é instalado na pasta `node_modules` do projeto.
>  - Adicionado ao arquivo `package.json` como uma dependência local.
>
> **Instalação Global**: O pacote é instalado em uma localização global no seu sistema, acessível de qualquer lugar. Usado para ferramentas de linha de comando.
>  ```bash
>  # Instalando o pacote 'nodemon' globalmente
>  npm install -g nodemon
>  ```
>  **Explicação:**
>  - O pacote `nodemon` é instalado globalmente, permitindo que você o execute de qualquer diretório.
>  - É útil para ferramentas que você usa em múltiplos projetos ou diretamente na linha de comando.
> 
> ### # Atualização de Pacotes
> Manter suas dependências atualizadas é crucial para segurança e funcionalidade.
>
> #### **Atualizando um Pacote Específico:**
> ```bash
> # Atualizando o pacote 'lodash' para a versão mais recente permitida pela SemVer
> npm update lodash
> ```
> **Explicação:**
> - Atualiza o pacote `lodash` para a versão mais recente compatível com a especificada em `package.json`.
>
> #### **Atualizando Todos os Pacotes:**
> ```bash
> # Atualizando todas as dependências do projeto
> npm update
> ```
> **Explicação:**
> - Atualiza todos os pacotes listados no `package.json` para a versão mais recente permitida pela SemVer.
> 
> #### **Atualização Forçada:**
> ```bash
> # Atualizando para a última versão disponível, mesmo que quebre a compatibilidade
> npm install lodash@latest
> ```
> **Explicação:**
> - Instala a versão mais recente do pacote `lodash`, ignorando a compatibilidade com a versão especificada anteriormente.
> 
> ### # Executando Scripts
> No `package.json`, você pode definir scripts personalizados para automatizar tarefas.
>
> #### **Definindo Scripts no package.json:**
> ```json
> "scripts": {
>   "start": "node app.js",
>   "test": "jest",
>   "build": "webpack --config webpack.config.js"
> }
> ```
> **Explicação:**
> - **`start`**: Executa `node app.js` para iniciar o aplicativo.
> - **`test`**: Executa `jest` para rodar testes automatizados.
> - **`build`**: Executa `webpack` para construir o projeto usando uma configuração específica.
> 
> #### **Executando Scripts:**
> ```bash
> # Executando o script 'start'
> npm run start
> 
> # Executando o script 'build'
> npm run build
> ```
> **Explicação:**
> - `npm run start` e `npm run build` executam os scripts definidos no `package.json`.
> - O script `start` pode ser executado apenas com `npm start` (sem `run`).
> 
> ### # npm Workspaces
> Os workspaces permitem gerenciar múltiplos pacotes em um único repositório (monorepo).
> 
> #### **Configuração de Workspaces:**
> ```json
> {
>   "name": "meu-monorepo",
>   "private": true,
>   "workspaces": [
>     "pacote-a",
>     "pacote-b"
>   ]
> }
> ```
> **Explicação:**
> - **`workspaces`**: Lista os diretórios `pacote-a` e `pacote-b` que contêm seus próprios `package.json`.
> - **`private: true`**: Garante que o repositório não será publicado no NPM.
> 
> **Benefícios:**
> - **Gerenciamento Centralizado**: Permite instalar e atualizar dependências para todos os pacotes de uma vez.
> - **Compartilhamento de Dependências**: Facilita o compartilhamento de dependências entre pacotes.
> 
> ### # Criando Pacotes
> Criar pacotes permite compartilhar código reutilizável com outros projetos ou com a comunidade.
>
> #### **Passos para Criar um Pacote:**
>
> 1. **Inicialize o pacote:**
>    ```bash
>    npm init
>    ```
>  - Gera um `package.json` onde você define o nome, versão, descrição e outras informações do pacote.
>
> 2. **Escreva o código:**
>  - Crie os arquivos e implemente a funcionalidade do seu pacote.
>
> 3. **Teste o pacote:**
>  - Teste seu código localmente para garantir que tudo funciona como esperado.
>
> 4. **Publique o pacote:**
>    ```bash
>    npm publish
>    ```
>  - Publica seu pacote no repositório do NPM para que outros possam instalá-lo e usá-lo.
>
> #### **Exemplo de package.json para um Pacote:**
> ```json
> {
>   "name": "meu-pacote",
>   "version": "1.0.0",
>   "description": "Um pacote exemplo",
>   "main": "index.js",
>   "scripts": {
>     "test": "echo \"Error: no test specified\" && exit 1"
>   },
>   "keywords": ["exemplo", "npm", "pacote"],
>   "author": "Seu Nome",
>   "license": "ISC"
> }
> ```
> **Explicação:**
> - **`name`**: Nome do pacote.
> - **`version`**: Versão inicial do pacote.
> - **`description`**: Descrição breve do que o pacote faz.
> - **`main`**: O ponto de entrada principal do pacote (arquivo principal).
> - **`scripts`**: Scripts relacionados ao desenvolvimento e teste.
> - **`keywords`**: Palavras-chave que ajudam na busca do pacote.
> - **`author`** e **`license`**: Informações sobre o autor e a licença do pacote.
>> ###### Você pode aprender mais sobre no artigo: [NPM - docs](https://docs.npmjs.com/)

<br>

> <h2 align="center">Tratamento de erros</h2>
>
> ### # System Errors (Erros de Sistema)
> Erros de sistema em Node.js são aqueles que resultam de falhas no ambiente de execução, como problemas de I/O (entrada/saída), falhas de rede, ou falta de recursos do sistema. Esses erros geralmente ocorrem durante operações assíncronas, como ao tentar acessar arquivos, se conectar a bancos de dados, ou comunicar-se com APIs externas.
> 
> #### **Exemplo:**
> Imagine que você tem um servidor Node.js que precisa ler um arquivo de configuração no momento em que inicia. Se o arquivo não estiver disponível (por exemplo, foi excluído ou o caminho está errado), isso resultará em um erro de sistema.
> ```javascript
> const fs = require('fs');
> 
> // Tentativa de ler um arquivo que não existe no sistema
> fs.readFile('/path/to/config.json', 'utf8', (err, data) => {
>    if (err) {
>        // Código do erro 'ENOENT' significa 'Error NO ENTry', indicando que o arquivo não foi encontrado
>        console.error('Erro ao ler o arquivo:', err.code, '-', err.message);
>        process.exit(1); // Encerra o processo devido a um erro crítico
>    } else {
>        // O arquivo foi lido com sucesso
>        console.log('Configurações carregadas:', data);
>    }
> });
> ```
> - `fs.readFile` tenta ler um arquivo de configuração.
> - Se o arquivo não for encontrado, um erro `ENOENT` será lançado, interrompendo o processo do servidor para evitar comportamento imprevisível.
> 
> ### # User Specified Errors (Erros Especificados pelo Usuário)
> Erros especificados pelo usuário são aqueles que você, como desenvolvedor, define explicitamente no código para indicar que uma condição específica não foi atendida. Isso é útil para validar dados ou garantir que certas pré-condições sejam satisfeitas antes de prosseguir.
>
> #### **Exemplo:**
> Considere que você tem uma função que deve dividir dois números, mas a divisão por zero é indefinida. Você pode lançar um erro especificado para evitar que isso aconteça.
> ```javascript
> function divide(a, b) {
>     if (b === 0) {
>         // Lança um erro se a tentativa for de dividir por zero
>         throw new Error('Divisão por zero não é permitida!');
>     }
>     return a / b;
> }
> 
> try {
>     // Tentativa de dividir 10 por 0, o que lançará um erro
>     const result = divide(10, 0);
>     console.log('Resultado:', result);
> } catch (err) {
>     // Captura o erro e exibe uma mensagem amigável
>     console.error('Erro ocorrido:', err.message);
> }
> ```
> - A função `divide` verifica se o divisor é zero.
> - Se for zero, um erro é lançado com uma mensagem clara.
> - O `try...catch` captura o erro e impede que o programa falhe sem controle.
>
> ### # Assertion Errors (Erros de Asserção)
> Asserções são condições que você espera que sejam verdadeiras durante a execução do código. No Node.js, você pode usar o módulo `assert` para garantir que essas condições sejam atendidas. Se uma asserção falhar, um erro de asserção é lançado, geralmente indicando que algo está muito errado no código.
> 
> #### **Exemplo:**
> Vamos supor que você está desenvolvendo uma função para somar dois números. Você quer garantir que a função sempre retorne o resultado correto.
> ```javascript
> const assert = require('assert');
> 
> function add(a, b) {
>     return a + b;
> }
> 
> // Teste de asserção para garantir que a função 'add' está funcionando corretamente
> const result = add(2, 2);
> assert.strictEqual(result, 4, 'O resultado esperado é 4, mas obtivemos um valor diferente');
> 
> console.log('Todos os testes passaram!');
> ```
> - A função `add` retorna a soma de dois números.
> - `assert.strictEqual` compara o resultado com o valor esperado.
> - Se o resultado não for 4, um erro de asserção é lançado com uma mensagem explicativa.
>
> ### # JavaScript Errors (Erros de JavaScript)
> Erros de JavaScript são os erros padrão que ocorrem no código JavaScript, como `TypeError`, `ReferenceError`, `SyntaxError`, entre outros. Em Node.js, esses erros podem ocorrer por diversas razões, como chamar uma função inexistente, acessar variáveis indefinidas, ou escrever código com sintaxe incorreta.
>
> #### **Exemplo:**
> Imagine que você tenta chamar uma função que não foi definida.
> ```javascript
> try {
>     // Tentativa de chamar uma função que não existe
>     nonExistentFunction();
> } catch (err) {
>     // Captura o erro ReferenceError e exibe uma mensagem de erro
>     console.error('Erro capturado:', err.name, '-', err.message);
> }
> ```
> - `nonExistentFunction()` tenta chamar uma função que não foi declarada.
> - O `try...catch` captura o `ReferenceError` e exibe uma mensagem clara para o desenvolvedor.
>
> ### # Uncaught Exceptions (Exceções Não Capturadas)
> Exceções não capturadas ocorrem quando um erro é lançado e não é tratado dentro de um bloco `try...catch`. No Node.js, isso pode causar o término do processo, o que pode ser desastroso em um ambiente de produção. Para evitar isso, você pode usar `process.on('uncaughtException')`, mas isso deve ser usado com cuidado.
>
> #### **Exemplo:**
> Suponha que você tenha um servidor que, por alguma razão, faz uma chamada a uma função que não existe, e esse erro não é capturado.
> ```javascript
> process.on('uncaughtException', (err) => {
>     // Captura exceções não tratadas
>     console.error('Exceção não capturada:', err.message);
>     // Finaliza o processo para evitar inconsistências
>     process.exit(1);
> });
> 
> // Função inexistente que causará um erro
> nonExistentFunction();
> ```
> - `process.on('uncaughtException')` captura exceções que não foram tratadas.
> - É importante encerrar o processo para evitar que o servidor fique em um estado inconsistente.
>
> ### # Handling Async Errors (Tratamento de Erros Assíncronos)
> Erros assíncronos ocorrem frequentemente em Node.js devido à natureza não bloqueante do ambiente. Ao trabalhar com callbacks, promessas, ou async/await, é crucial lidar corretamente com erros para evitar que o aplicativo falhe silenciosamente ou tenha comportamentos inesperados.
> 
> #### **Exemplo com Callback:**
> Suponha que você está lendo um arquivo que pode não existir.
> ```javascript
> const fs = require('fs');
> 
> // Tentativa de ler um arquivo que pode não existir
> fs.readFile('/path/to/file.txt', 'utf8', (err, data) => {
>     if (err) {
>         // Erro na leitura do arquivo
>         console.error('Erro ao ler o arquivo:', err.message);
>         return;
>     }
>     console.log('Conteúdo do arquivo:', data);
> });
> ```
>
> #### **Exemplo com Promises:**
> Agora, usando promessas para lidar com o mesmo caso.
> ```javascript
> const fs = require('fs').promises;
> 
> async function readFile() {
>     try {
>         // Tentativa de ler um arquivo
>         const data = await fs.readFile('/path/to/file.txt', 'utf8');
>         console.log('Conteúdo do arquivo:', data);
>     } catch (err) {
>         // Lida com o erro de forma assíncrona
>         console.error('Erro ao ler o arquivo:', err.message);
>    }
> }
> 
> readFile();
> ```
> - `fs.readFile` com callbacks e promessas demonstra duas abordagens para lidar com erros assíncronos.
> - Em ambos os casos, o erro é capturado e tratado para evitar falhas silenciosas.
> 
> ### # Callstack / Stack Trace (Pilha de Chamadas / Rastreamento de Pilha)
> A pilha de chamadas, ou stack trace, é um relatório que mostra a sequência de chamadas de função que levou a um erro. Em Node.js, a stack trace é extremamente útil para depuração, pois ajuda a identificar onde exatamente o erro ocorreu e como o fluxo do programa chegou a esse ponto.
> 
> #### **Exemplo:**
> Imagine que você tem várias funções aninhadas e uma delas lança um erro.
> ```javascript
> function functionOne() {
>     functionTwo();
> }
> 
> function functionTwo() {
>     functionThree();
> }
> 
> function functionThree() {
>     // Lança um erro propositalmente
>     throw new Error('Algo deu errado na função três!');
> }
> 
> try {
>     functionOne();
> } catch (err) {
>     // Exibe a stack trace completa para ajudar na depuração
>     console.error('Stack Trace:', err.stack);
> }
> ```
> - As funções `functionOne`, `functionTwo`, e `functionThree` são chamadas em sequência.
> - Quando `functionThree` lança um erro, a stack trace mostra todas as funções chamadas antes do erro ocorrer.
> 
> ### # Using Debugger (Usando Depurador)
> Node.js inclui ferramentas de depuração que permitem aos desenvolvedores examinar o estado do programa durante a execução. O depurador pode ser usado para definir pontos de interrupção, inspecionar variáveis, e seguir o fluxo do código passo a passo. Isso é essencial para entender o comportamento do código e localizar erros.
> 
> #### **Exemplo:**
> Vamos ativar o depurador em um script Node.js.
> ```javascript
> function add(a, b) {
>     debugger; // Define um ponto de interrupção
>     return a + b;
> }
>
> const result = add(5, 3);
> console.log('Resultado:', result);
> ```
> - O `debugger` é uma palavra-chave que, ao ser atingida, pausa a execução do código.
> - Ao rodar o código com `node inspect script.js`, o depurador é ativado, permitindo examinar o estado do programa no ponto de interrupção.
>> ###### Você pode aprender mais sobre no artigo: [MDN - Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)
