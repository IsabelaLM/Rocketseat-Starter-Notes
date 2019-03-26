# Rocketseat-Starter-Notes
Resumo do curso Starter de JS e ES6

Stack:
* ReactJS - Front
* NodeJS - Back
* React Native - mobile


#JS - Introdução


https://rocketseat.com.br/videos/curso-javascript-basico-do-zero?utm_source=mautic&utm_medium=funil&utm_campaign=curso_javascript_basico#1/1




## Conteúdos:


- Variáveis
- Funções
- Condicionais
- Estruturas de repetição
- Manipulação de DOM 
- Requisições assíncronas > pegar informações do backend sem precisar recarregar a página
- App do zero


## Variáveis


- Não tem tipagem estática (não precisa definir se é string, int, float, etc)
- Possui tipagem dinâmica
- ex:


      var nome = "Isabela";
      nome = 10;


- algumas variáveis possíveis:


      // string
      var nome = "Isabela";


      // int
      var idade = 31;


      // float
      var peso = 80.5;


      // boolean
      var humano = true;


      // vetor
      var amigos = ['Mau', 'Marcos', 'Kalleu'];


      // objeto
      var amigo = {
            nome: 'Mau',
            idade: 38,
            peso: 70,
            humano: true
      };


## Operações Matemáticas


- igual às outras linguagens, nada novo


      var x = 10, y = 5;


      var result = x + y;


      console.log(result);


## Funções


- igual também, com escopo mas sem tipagem estática


      function soma(numero1, numero2){
            var resultado = numero1 + numero2;
            return resultado;
      }


      var resultado = soma(1, 2)
      console.log(resultado); // 3


## Condicionais


- É possivel verificar o valro, com "==" e o tipo também, com "===":


      if (1 == "1") {}  // retorna true
      if (1 === "1") {} // retorna false


- o resto é igual (if e switch)


      function retornaSexo(sexo) {
            // M, F
            // Masculino, Feminino, Outro


            if (sexo === 'M'){
                  return 'Masculino';
            }
            else if (sexo === 'F') {
                  return 'Feminino';
            }
            else {
                  return 'Outro';
            }


            // ----- OU -----


            switch (sexo) {
                  case 'M':
                        return 'Masculino';
                  case 'F':
                        return 'Feminino';
                  default:
                        return 'Outro';
            }
      }


      var resultado = retornaSexo('M');
      consolo.log(resultado);




## Operadores Lógicos


- igual tb: AND, OR, NOT > &&, ||, !=, !==
- armazenar valor da comparação de forma resumida:


      var sexo = 'M';
      var masculino = (sexo === 'M'); //nem precisa dos parênteses
      console.log (masculino);


## Condição Ternária


- se aplica quando temos apenas um if e else:


       var sexo = 'M';


       var resultado = (sexo === 'M') ? 'Masculino' : 'Feminino';
       console.log (resultado);


## Estruturas de Repetição


- igual tb: for e while


      for (var i = 0; i <= 100; i++) {
            console.log(i);
      }


      // ----- OU -----


      var j = 0;
      while (j <= 100) {
            console.log(j);


            j++;
      }


- o while normalmente é utilizado quando não sabemos exatamente quantas vezes o loop vai ser executado:


      var j = 219345872; // um número bem grande...
      while (j > 50) {
            console.log(j);


            j /= 5;
      }


- Um equivalente do foreach:


      var todos = [
            'fazer cafe',
            'estudar JS',
            'ver videos tutoriais'
      ];


      function renderTodos() {
            for (todo of todos) {  // pega cada objeto
                  console.log(todo);
            }
      }
    
    var person = {fname:"John", lname:"Doe", age:25}; 
    var text = "";
    var x;
    for (x in person) { // pega o indice de cada objeto
        text += person[x];
    }




## Intervalo e Timeout


- Intervalo: executa a função passada no parâmetro acada intervalo de tempo definido (em ms):


      function exibeAlgo() {
            console.log('Hello World');
      }


      setInterval(exibeAlgo, 1000); // vai chamar a função "exibeAlgo" a cada segundo


 - Timeout: vai executar uma única vez após o delay determinado:


      setTimeout(exibeAlgo, 5000); // vai chamar a função "exibeAlgo" apenas 5 segundos depois de carregada a página




# Manipuando a DOM


## Eventos Inline


- Função Javascript alterando o comportamento de um botão no DOM:


      <html>
            <head>
            </head>


            <body>
                  <div id="app">
                        <button onclick='exibeAlerta()'>Me Pressione</button>
                  </div>


                  <script>
                        function exibeAlerta() {
                              alert('Botão foi clicado!!!')
                        }
                  </script>
            </body>
      </html>


## Trabalhando com a DOM


- Referenciar elementos da DOM com JS


      <body>
            <div id="app">
                  <input type"text" name="nome" id="nome" />
                  <button class="botao">Adicionar</button>
            </div>


            <script>
                  var inputElement = document.getElementById('nome'); // como id é único, retorna apenas 1 elemneto
                  // ------ OU ------
                  var inputElement2 = document.getElementsByTagName('input'); // sempre retorna um array
                  // ------ OU ------
                  var inputElement3 = document.querySelector('body div#app input'); // passa o caminho do elemento como input
                  // ------ OU ------
                  var inputElement4 = document.querySelector('input[name='nome']'); // referenciando uma propriedade do elemento
                  // ------ OU ------
                  var inputElement5 = document.querySelectorAll('input'); // retorna um array


                  var btnElement = document.querySelector('button.botao');


                  btnElement.onclick = function() {
                        alert('botao clicado!'); // como no exemplo anterior, mas usando o "onclick" no script ao invés de usar no DOM (evitando, assim, "sujar" o client side com elementos de javascript).


                        // ------ OU ------


                        var text = inputElement4.value; // recupera o valor inserido no campo
                        alert(text);
                  }
            </script>
      </body>


      Obs: "document." é o objeto global que referencia a árvore de elementod da DOM
      Obs2: "classe" é referenciada com "." e "id" com "#"


## Criando e Posicionando Elementos


- Além de referenciar elementos, é possível criar elementos através do Javascript


      <body>
            <div id="app">
            </div>


            <script>
                  var linkElement = document.createElement('a'); // cria um elemento do tipo "link", cuja tag é "a"


                  linkElement.setAttribute('href', 'http://google.com')
                  // ------ OU ------
                  linkElement.href = 'http://google.com';


                  var textElement = document.createTextNode('Acessar site...');
                  linkElement.appendChild(textElement);


                  var containerElement = document.querySelector('#app');
                  containerElement.appendChild(linkElement);
            </script>
      </body>


## Alterando o Estilo dos Elementos


- Modificar o estilo de um elemento da DOM


      <body>
            <div id="app">
                  <div class="box"></div>
            </div>


            <script>
                  var boxElement = document.querySelector('.box');


                  boxElement.style.width = 100;
                  boxElement.stle.bacgroundColor = '#f00';


            </script>
      </body>




# Aplicação Todos


## Estrutura da Aplicação


- Criar um novo arquivo (ex.: todos.js) que só contém a parte de script:


      <body>


            <script> src="todos.js"</script>
      </body>


## Outros Pontos Interessantes da Aplicação Exemplo


- Criar um link, e atribuir uma função, com parâmetros à esse link;


      for (todo of todos) {
            // ...


            var linkElement = document.createElement('a');
            linkElement.setAttribute('href', '#');


            var pos = todos.indexOf(todo);
            linkElement.setAttribute('onclick', 'deleteTodo(' + pos + ')');


            // ...
      }


      function deleteTodo(pos) {
            todos.splice(pos, 1);   // remove o elemento que está na posição "pos"
      }




## Salvando Dados no Local Storage


- Usar o armazenamento local (Local Storage) para salvar informações; como o localStorage (variável global) não entende array, é necessário converter o vetor "todos" antes de salvar a informação (no caso, em JSON - JavaScript Object Notation)


      function saveToStorage() {
            localStorage.setItem('list_todos', JSON.stringfy(todos));
      }


      // E para recuperar os valores do Local Storage:


      var todos = JSON.parse(localStorage.getItem('list_todos'));


      // E para definir valores padrão, caso o localStorage esteja vazio:


      var todos = JSON.parse(localStorage.getItem('list_todos')) || [];




      obs: dá pra ver o localStorage pelo console do browser!




# Javascript Assíncrono


## Requisição AJAX


- Requisição assíncrona realizada em algum backend (requisita informação sem precisar atualizar a página)


      var xhr = new XMLHttpRequest();


      xhr.open('GET', 'http://api.github.com/users/diego3g'); // Isso jé é assíncrono
      xhr.send(null);


      xhr.onreadystatechange = function() {
            if (xhr.readyState === 4) { // "4" significa que a resposta voltou
                  console.log(JSON.parse(xhr.responseText)); // o retorno da requisição é um JSON
            }
      }


## Promises


- Promises são códigos que não vão influenciar na linha do tempo do javascript


      var minhaPromise = function() {
            return new Promise(function(resolve, reject) { // "resolve" e "reject" também são funções
                  // código aqui...
            }); 
      }


      // utilizando o exemplo anterior:


      var minhaPromise = function() {
            return new Promise(function(resolve, reject) { // "resolve" e "reject" também são funções
                  
                  var xhr = new XMLHttpRequest();
                  xhr.open('GET', 'http://api.github.com/users/diego3g'); // Isso jé é assíncrono
                  xhr.send(null);


                  xhr.onreadystatechange = function() {
                        if (xhr.readyState === 4) { // "4" significa que a resposta voltou
                              if (xhr.status === 200) { // "200" significa que retornou com sucesso
                                    resolve(JSON.parse(xhr.responseText)); // "resolve" é um dos parametros da "Promise"
                              } else {
                                    reject('Erro na requisição'); // "reject" é um dos parametros da "Promise"
                              }
                        }
                  }
            }); 
      }


      var result = minhaPromise();
      console.log(result); // vai retornar com o estado de "pending" porque a requsição ainda não voltou quando passou por esse ponto do código


      // Para acessar o resultado do request, fazemos assim então:
      minhaPromise()
            .then(function(response) { // ".then" vai ser executado quando chamarmos o "resolve" na promisse.
                  console.log(response);
            })
            .catch(function(error) { // ".catch" vai ser chamado quando chamarmos o "reject" na promisse.
                  console.warn(error);
            });


## Utilizando Axios


- Biblioteca para fazer as requisições assíncronas do JS (no lugar de utilizar XMLHttpRequest)


      <html>
            <head>
            </head>
            <body>
                  <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
                  <script src="main.js"></script>
            </body>
      </html>


      obs: precisa importar o axios antes do nosso script principal!


- O Axios nada mais é do que um wrapper em cima do XMLHttpRequest


      axios.get('http://api.github.com/users/diego3g')
            .then(function(response) {
                  console.log(response);
            })
            .catch(function(error) {
                  console.warn(error);
            });


- O Axios já entende que a resposta é um JSON e já converte ela para JavaScript


      axios.get('http://api.github.com/users/diego3g')
            .then(function(response) {
                  console.log(response.data.avatar_url); // não precisa fazer o parse!!!
            })
            .catch(function(error) {
                  console.warn(error);
            });




# Conceitos do ES6+


## Introdução


- ES6 =  ECMAScript, versão 6 (ano 2015)
- Quem formula as novas funcionalidades do JS
- Adicionam novas regras todos os anos
- Babel: navegadores são lentos para seguir as atualizações de funcionalidades, então podem não entender todas essas funcionalidades. O Babel pega o código ES6 e tranpila (reescreve) essas funcionalidades de uma maneira que os browsers intendam (ex.: o Babel converte classes, conceito que não exite em JS, para um modelo de funções).


- Alguns pontos que serão vistos:
      - Webpack > servidor para conseguirmos ter o live reload (atualizar automaticamente); ativa automaticamente o Babel
      - Classe
      - Arrow function > novo modelo para criar funções anônimas
      - Desestruturação > forma de recuperar propriedades de dentro de um objeto e de um array
      - Rest/spread > formas de manipular as propriedades dentro de objetos (copiar, duplicar, etc.)
      - Import/export > importar e exportar funcionalidades de um arquivo JS para outro
      - Async/Await > nova API de trabalhar de forma assincrona (mais simples e menod verbosa que Axios e promises)




## Instalando o Node & Yarn


- Node.js > instalar > verificar se está instalado fazendo no terminal "node -v"
- Yarn > gerenciador de pacotes do JS > instalar > no ternimal, fazer "yarn -v"




## Confirgurando Babel


- dentro da raiz do nosso projeto:
      
      Terminal > yarn init
      (pode dar "enter" para todas as perguntas)


      Terminal > yarn add @babel/cli
      (para usar o babel com linhas de comando)


      Terminarl > yarn add @babel/preset-env


- Com isso, são criados na raiz do projeto a pasta "node_modules" e o arquivo "yarn.lock"


- Se for utilizar o git como sistema de versão, já criar um arquivo ".gitignore" na raiz do projeto e escrever dentro dele "node_modules/"


- Para confiugrar o babel:
      - criar um arquivo ".babelrc" na raiz do projeto com:


      {
            "presets": ["@babel/preset-env"]
      }


- Criar os arquivos "index.html" e "main.js"


- Dentro do arquivo package.json, adicionar:


      ...


      "scripts": {
            "dev": "babel ./main.js -o ./bundle.js"
      }


- Adicionar mais uma dependência
      
      Terminal > yarn add @babel/core


- Para testar se está tudo ok:
      
      Terminal > yarn dev


- Depois desse comando, um novo arquivo é criado ("bundle.js") com o código do "main.js" convertido pelo babel


      obs.: se colocarmos um "-w" no comando "dev" ( "dev": "babel ./main.js -o ./bundle.js -w" ), essa conversão é feita automaticamente a cada alteração do arquivo "main.js"


- IMPORTANTE: no "index.html", adicionar a tag script com o "src" apontando para o "bundle.js" (e não para o "main.js")    




## Classes


- Tem contructor, this, methods, etc...


- ex.: (no "main.js")


      class TodoList {
            constructor() {   // pode criar novas variáveis aqui dentro
                  this.todos = [];
            }


            addTodo() {   // um método da classe
                  this.todos.push('Novo todo');
                  console.log(this.todos);
            }
      }


      const MinhaLista = new TodoList();


      document.getElementById('novotodo').onclick = function() {   // botão "novotodo" criado lá no html
            MinhaLista.addTodo();
      }


- Herança:


      class List {
            constructor() {
                  this.data = [];
            }


            add(data) {
                  this.dadta.push(data);
                  console.log(this.data);
            }
      }


      class TodoList extends List{
            constructor() {
                  super();   // chama o contrutor pai
            }
      }


      const MinhaLista = new TodoList();


      document.getElementById('novotodo').onclick = function() {   // botão "novotodo" criado lá no html
            MinhaLista.add('Novo todo');
      }      


- Métodos estáticos (não precisa dar "new" na classe para usar um método dela)


      class Matematica {
            static soma(a, b) {
                  return a + b;
            }
      }


      console.log(Matematica.soma(1, 2)); // não precisa dar "new" em um objeto da classe antes de usar o método


      obs.: o método estático enxerga os outros elementos da classe, então, no primeiro exmplo, o método "addTodo()" não poderia ser estático pois não seria possível adicionar um elementos ao array this.todos, já que ele poderia não ter sido criado.




## Const & Let


- Uma variável "const" não pode ter ser valor alterado; porém, pode ter ser valor mutado


      const num = 1;
      num = 3; // ---> dá erro


      const usuario = { nome: 'Diego' };
      usuario.nome = 'Cleiton'; // ---> isso é uma mutação e é permitida


- Através da palavra-chave "let" podemos declarar variáveis com escopo de bloco (como nas outras linguagens); o "var" tem um comportamento um pouco diferente (http://blog.alura.com.br/entenda-diferenca-entre-var-let-e-const-no-javascript/).


      function test(x) {
            let y = 2;


            if (x > 5) {
                  let y = 4;
                  console.log(x, y);
            }
      }


      teste(10); // 10 4




## Operações em Array


- Algumas facilidades do EC6 para lidar com vetores:


      const arr = [1, 3, 4, 5, 8, 9];


      // ---> "map" percorre o vetor e retorna alguma coisa de dentro
      
      const newArr = arr.map(function(item) {
            return item * 2;
      });


      console.log(newArr); // [2, 6, 8, 10, 16, 18]


      ------ OU ------


      const newArr = arr.map(function(item, index) {
            return item + index;
      });


      console.log(newArr); // [1, 4, 6, 8, 12, 14]






      // ---> "reduce" é uma forma de consumirmos todo o vetor e transformar em uma única variável


      const sum = arr.reduce(function(total, next) {
            return total + net; // a cada ciclo, total e next assumem os seguntes valores: 0, 1 | 1, 3 | 4, 4 | ...
      });


      console.log(sum); // 30




      // ---> "filter" filtra informações do array


      const filter = arr.filter(function(item) {
            return item % 2 === 0; // retorna apenas os itens divisiveis por 2
            // obs.: essa expressão do retorno do filter precisa, obrigatóriamente, retornar true ou false!
      });


      console.log(filter); // [4, 8]




      // ---> "find" é para retornar se existe certa informação dentro do array ou para encontrar determinada informação


      const find = arr.find(function(item) {
            return item === 4;
      });


      console.log(find); // 4 (retorna o valor, se encontrar; se não encontrar, retorna "undefined").




## Arrow Functions


- São mais usadas em casos de callback, ou seja, passagem de função para outra função, reduzindo a verbosidade do código
- Servem, por exemplo, para substituir funções anônimas, como esta:


      const arr = [1, 3, 4, 5, 6];
      
      const newArr = arr.map(function(item) { // função anonima
            return item * 2;
      });


      ------ OU ------


      // ---> substituindo por arrow function:
      
      const newArr = arr.map((item) => { // remove a keywork "funcion" e coloca um "=>" logo depois do parametro!
            return item * 2;
      });


      ------ OU ------


      // ---> simplificando mais
      
      const newArr = arr.map(item => { // quando a function recebe apenas 1 parametro, podemos retirar os parenteses também
            return item * 2;
      });


      ------ OU ------


      // ---> simplificando ainda mais:
      
      // quando o corpo da function só tem 1 linha (não tem muitos processamentos), podemos tirar as chaves, a palavra "return" e o ";"
      const newArr = arr.map(item => item * 2);


- Também é possivel usar arrow function pra funções não anonimas, mas não é recomendado:


      function teste() {


      }


      // ficaria:


      const teste = () => {


      };


## Valores padrão em parâmetros


- Para não dar o erro "NaN" quando chamamos uma função sem todos os parâmetros:


      function soma(a = 3, b = 6) {
            return a + b;
      }


      console.log(soma(1)); // 7
      console.log(soma());  // 9


      ------ OU ------


      // ---> com arrow function ficaria assim:


      const soma = (a = 3, b = 6) => a + b;


      console.log(soma(1)); // 7
      console.log(soma());  // 9




## Desestruturação


- Pegar informações de objetos de forma mais simplificada:


      const usuario = {
            nome: 'Diego',
            idade: 23,
            endereco: {
                  cidade: 'Rio do Sul',
                  estado: 'SC',
            },
      };


      const nome = usuario.nome;
      const idade = usuario.idade;


      ------ OU ------


      // simplificado ficaria assim:


      const { nome, idade } = usuario;


      console.log(nome);
      console.log(idade);


- se incluirmos mais uma informação:


      const nome = usuario.nome;
      const idade = usuario.idade;
      const cidade = usuario.endereco.cidade;


      ------ OU ------


      // simplificado ficaria assim:


      const { nome, idade, endereco: { cidade } } = usuario;


      console.log(nome);
      console.log(idade);
      console.log(cidade);


- outras aplicações:


      function mostraNome(usuario) {
            console.log(usuario.nome);
      }


      mostraNome(usuario);


      ------ OU ------


      // simplificado ficaria assim:


      function mostraNome({ nome }) {
            console.log(nome);
      }


      mostraNome(usuario);


      ------ OU ------


      function mostraNome({ nome, idade }) {
            console.log(nome, idade);
      }


      mostraNome(usuario);




## Operadores rest/spread


- Antes, precisamos adicionar o plugin


      1. Terminal > yarn add @babel/plugin-proposal-object-rest-spread


      2. Adicionar no arquivo ".babelrc"


      {
            "presets": ["@babel/preset-env"],
            “plugins": ["@babel/plugin-proposal-object-rest-spread"]
      }


      3. Cancela (ˆC) e roda (yarn dev) o yarn que estava monitorando as mudanças.


- Aplicações:


      // REST - pegar o resto das propriedades


      const usuario = {
            nome: 'Diego',
            idade: 23,
            empresa: 'Rocketseat'
      };


      const { nome, ...resto } = usuario;


      console.log(nome);
      console.log(resto); // vai mostrar as outras informações do objeto usuário, sem o nome.




      // outro exemplo:


      const arr = [1, 2, 3, 4];


      const [ a, b, ...c ] = arr; // desestruturação de um array com aplicação de rest!


      console.log(a); // 1
      console.log(b); // 2
      console.log(c); // [3, 4]




      // outra aplicação do rest é em parâmetros de função:


      function soma(a, b) {
            return a + b;
      }


      console.log(soma(1, 3));


      // se quiser adicionar mais um número na soma, temos que reescrever a função; para evitar isso, usamos rest:


      function soma(...params) {   // params passa a ser um array com os inputs passados como parâmetros
            return params.reduce((total, next) => total + next);  // podemos usar o reduce para retornar a soma
      }
      console.log(soma(1, 3, 4)); // 8




      // SPREAD - repassa as informações de uma estrutura para outro objeto


      const arr1 = [1, 2, 3];
      const arr1 = [4, 5, 6];


      const arr3 = [ ...arr1, ...arr2 ];


      console.log(arr3); // [1, 2, 3, 4, 5, 6]




      // outra aplicaçãp: copiar um objeto modificando um dos parametros


      const usuario1 = {
            nome: 'Diego',
            idade: 23,
            empresa: 'Rocketseat'
      };


      const usuario2 = { ...usuario1, nome: 'Gabriel' };




## Template Literals


- Incluir variáveis dentro de strings


      // normalmente, fazemos a concatenação assim:


      const nome = 'Diego';
      const idade = 23;


      console.log('Meu nome é ' + nome + ' e tenho ' + idade + ' anos.');


      // para simplificar, utilizamos os símbolos " ` " e " ${  } "


      console.log(`Meu nome é ${nome} e tenho ${idade} anos.`);




## Object Short Syntax


- Sintaxe curta de objetos


      const nome = 'Diego';
      const idade = 23;


      const usuario = {
            nome: nome,
            idade: idade,
            empresa: 'Rocketseat',
      };


      // com o ES6, quando o nome da variável é igual ao nome da propriedade dentro do objeto, podemos escrever de forma simplificada:


      const usuario = {
            nome,
            idade,
            empresa: 'Rocketseat',
      };




# Webpack Server


## Configurando Webpack


- Serviço que nos disponibiliza várias formas de trabalharmos com vários arquivos .js (e imagens, e pastas) no projeto.
- No fim, todos esses arquivos e pastas ainda serão resumidos a um único arquivo bundle.js
- Para configurar o webpack, fazemos:


      No arquivo "package.json" mudar:
            'dependencies' para 'devDependencies'




      Terminal > yarn add webpack webpack-cli -D


- Criar um arquivo "webpack.config.js" de configurações do webpack e escrever:


      module.exports = {
            entry: './main.js',
            output: {
                  path: __dirname,
                  filename: 'bundle.js',
            },
            module: {
                  rules: [
                        {
                              test: /\.js$/,
                              exclude: /node_modules/,
                              use: {
                                    loader: 'babel-loader',
                              }
                        }
                  ],
            },


      }


      obs.: entry é o arquivo principal
            output é o nome do arquivo pra qual devemos mandar o código convertido
            module rules mostra como o webpack deve se comportar quando tentarmos importar um novo arquivo js
            expressão regular " / \.js $/ " para verificar se é um arquivo .js ( '/' início da regexp '$/' fim da regexp)


      Terminal > yarn add babel-loader -D


- Para executar o webpack:


      No arquivo "package.jason", trocar o conteudo do "dev" (que era para executar o babel) para:


      "scripts": {
            "dev": "webpack --mode=development -w"
      }


      Terminal > yarn dev
      (para ver se rodou tudo direitinho)


      se der erro, rodar o seguinte comando e depois rodar o "yarn dev" novamente:
      Terminal > yarn add babel-loader@8.0.0-beta.0 -D
      Terminal > yarn dev


- Para testar se o webpack está funcionando:
      
      criar um novo arquivo "funcoes.js" e escrever:


            export function soma(a, b) {
                  return a + b;
            }


      e no arquivo "main.js", escrever:


            import { soma } from './funcoes';


            console.log(soma(1, 2));




## Import/export


- Continuando o último exmplo:


      No arquivo "funcoes.js" e escrever:


            export function soma(a, b) {
                  return a + b;
            }


            export function sub(a, b) {
                  return a - b;
            }


      e no arquivo "main.js", escrever:


            import { soma, sub } from './funcoes';


            console.log(soma(1, 2));
            console.log(sub(4, 2));


- Em react, normalmente um arquivo só vai ter uma função ou classe; nesse caso, podemos usar a palavra default:


      Em um arquivo "soma.js" e escrever:


            export default function soma(a, b) {
                  return a + b;
            }


      e no arquivo "main.js", escrever:


            import soma from './soma';


            console.log(soma(1, 2));


- Também é possível renomear as funções quando elas são importadas:


      mantendo os mesmos arquivos "soma.js" e "funcoes.js", fazemos assim no "main.js":


      import { soma as somaFunction, sub } from './funcoes'; // nesse caso é necessário usar a palavra "as" para renomear
      import somaDefault from './soma'; // com os exports defaults, é só renomear aqui


      console.log(somaFunction(1, 2));
      console.log(sub(4, 2));
      console.log(somaDefault(1, 2));


- No mesmo arquivo, podemos ter 1 export default e outros exports comuns


      No arquivo "funcoes.js" e escrever:


            export defaut function soma(a, b) {
                  return a + b;
            }


            export function sub(a, b) {
                  return a - b;
            }


      e no arquivo "main.js", escrever:


            import soma, { sub } from './funcoes';


            console.log(soma(1, 2));
            console.log(sub(4, 2));


- também é possivel exportar todas funções de uma só vez:


      (sem usar o default no arquivo "funcoes.js" , por exemplo)
      no arquivo "main.js", escrever:


            import * as funcoes from './funcoes';


            console.log(funcoes); // mostra que esse objeto contém todas as funções do arquivo js


            console.log(funcoes.soma(1, 2));
            console.log(funcoes.sub(4, 2));




## Webpack Dev Server


- Primeiro nós vamos organizar nossa estrutura de arquivos em pastas:


      - Pasta "src" > vai conter todos os arquivos js que iremos utilizar em nossa aplicação > ex.: "main.js"
      - Pasta "public" > todos os arquivos que não vamos trabalhar diretamente com o webpack (ou seja, que não precisam ser monitorados por ele) > ex.: "index.html"


      - Com isso, precisamos fazer algumas alterações no arquivo "webpack.config.js":


            module.exports = {
                  entry: './src/main.js',
                  output: {
                        path: __dirname + '/public',
            
            ... (o resto fica igual)


- Instalar o dev server (para trabalhar com o projeto offline):
      
      Terminal > yarn add webpack-dev-server -D


      Acicionar “devServer" no cconfig do webpack:


      module.exports = {
            entry: './src/main.js',
            output: {
                  path: __dirname + '/public',
                  filename: 'bundle.js',
            },
            devServer: {
                  contentBase: __dirname + '/public'
            },
            module: {
                  rules: [
                        {
                              test: /\.js$/,
                              exclude: /node_modules/,
                              use: {
                                    loader: 'babel-loader',
                              }
                        }
                  ],
            },


      }


- No "package.json", alterar o script dev:
      
      "scripts": {
            "dev": "webpack-dev-server --mode=development"
      }


      Terminal > yarn dev


- Agora conseguimos acessar nosso projeto no browser através do endereço "http://localhost:8080/"


- O arquivo "bundle.js" pode ser excluido da nossa pasta; ele deve continuar presente lá no index.html, mas o webpack faz com que ele não precise aparecer nos arquivos do nosso projeto (isso no modo de desenvolvimento local)


- Quando quisermos jogar nosso projeto pra online, para ter o arquivo "bundle.js", fazemos:


      No "package.json", alterar o script:
      
      "scripts": {
            "dev": "webpack-dev-server --mode=development"
            "build": "webpack --mode=production"
      }


      Terminal > yarn build


- Com o webpack-dev-server rodando, o reload da página acontece automaticamente assim que salvamos o arquivo js!!! Ele monitora toda vez que acontecer alguma mudança na pasta "src", ele dá o refresh na página para vermos essa mudança.




# Async/await


## Async/await


- Normalmente criamos e utilizamos uma promise da seguinte forma:


      const minhaPromise = () => new Promise((resolve, reject) => {
            setTimeout(() => { resolve('OK') }, 2000);
      });


      minhaPromise()
            .then(response => {
                  console.log(response);
            })
            .catch(err => {


            });


- Com async/await fica assim:


      const minhaPromise = () => new Promise((resolve, reject) => {
            setTimeout(() => { resolve('OK') }, 2000);
      });


      async function executaPromise() {   // sempre tem que ter uma função em volta
            const response = await minhaPromise();   // equivale ao ".then"


            // a próxima linha depois de um await só vai ser executada depois que o await terminar.


            console.log(response);
      }


      executaPromise();


- Precisamos instalar um plugin antes para funcionar:


      Terminal > yarn add @babel/plugin-transform-async-to-generator -D
      Terminal > yarn add @babel/polyfill -D


      Adicionar no .babelrc:


      {
            "presets": ["@babel/preset-env"],
            "plugins": [
                  "@babel/plugin-proposal-object-rest-spread",
                  "@babel/plugin-transform-async-to-generator"
            ]


      }


      Já o polyfill vai no arquivo "webpack.config.js":


      module.exports = {
            entry: ['@babel/polyfill', './src/main.js'],


            ...
            (o resto é igual)


      Depois, cancela e roda o dev de novo:


      Terminal > yarn dev


- Fica mais simples do que com a sintaxe ".then()":


      async function executaPromise() {
            console.log(await minhaPromise());
            console.log(await minhaPromise());
            console.log(await minhaPromise());
            // De 2 em 2 segunsdos imprime "OK" no console


            // o equivalente com ".then()", seria:
            minhaPromise().then(response => {
                  console.log(response);


                  minhaPromise().then(response => {
                        console.log(response);


                        minhaPromise().then(response => {
                              console.log(response);
                        })
                  })
            })
      }


      executePromise();


- Quando criamos uma async function, automaticamente essa função também vira uma Promise


- Também é possivel usar o async/await com uma arrow function:


      const executaPromise = async () => {
            console.log(await minhaPromise());
            console.log(await minhaPromise());
            console.log(await minhaPromise());
      };


      executaPromise();




## Configurando Axios


- Usaremos o Axios para acessar APIs


      Terminal > yarn add axios
      (como não é uma dependencia de dev, não adicionamos o "-D" no fim)


- Acessar a API do github, por exemplo:


      No arquivo "main.js":


      import axios from 'axios';


      class Api {
            static async getUserInfo(username) {
                  const response = await axios.get(`https://api.github.com/users/${username}`);


                  console.log(response);
            }
      }


      Api.getUserInfo('diego3g');


- Para pegar os casos de erro com async/await, precisamos adicionar os blocos try/catch (ex.: nome do usuário não existe):


      class Api {
            static async getUserInfo(username) {
                  try {
                        const response = await axios.get(`https://api.github.com/users/${username}`);


                        console.log(response);
                  } catch(err) {
                        console.warn('Erro na API');
                  }
            }
      }


      Api.getUserInfo('diego3g1230i39'); // usuário que não exista...




# Aplicação com ES6


## Estrutura e estilos


- Criou o conteudo do index.html com a estrutura básica




## Adicionar Repositórios


- Criou nova classe "App" no .js para acessar os elementos do html
- Essa classe é a principal (e para esse exemplo é provavelmente a única)
- Para rodar o contructor da classe temos que instancia-la:


      const myApp = new App();


      obs.: como não vamos usar o objeto da classe para mais nada além de chamar o contructor, podemos fazer assim:


      new App();


- Lembrar de chamar o método "preventDefault()" no "onsubmit" do botão do forma (para evitar que a página seja recarregada sempre que o botão for clicado, que é o comportamento default);




## Render em Tela


- O "map" serve para percorrer o array e alterar cada elemento de uma forma; já o "forEach" só percorre.




## Buscando da API


- Criou um novo arquivo "api.js" para fazer a parte de configuração do axios
- Conseguimos criar uma base url para a api e, apartir dessa definição, todas as requisições vão partir desse endereço


      - no arquivo "api.js":


      import axios from 'axios';


      const api = axios.create({
            baseURL: 'https://api.github.com',
      });


      export default api;


      - no arquivo "main.js", fazer o import:


      import api from './api';


- Bons exemplos no video das vantagens/facilidades de se usar as seguintes features do ES6: template literals, desestruturação e object short sintax!




## Loading e Error


- Quando criamos um elemento pelo js, podemos também adicionar um atributo id; isso é bom para quando quisermos acessar esse elemento em outra parte do código (para remover o elemento "loading", por exemplo)


      // método dentro da classe App:
      setLoading(loading = true) {  // valor default
            if (loading === true) {
                  let loadingEl = document.createElement('span');
                  loadingEl.appendChild(document.createTextNode('Carregando...'));
                  loadingEl.setAttribute('id', 'loading'); // o id desse elemento é "loading"


                  this.formEl.appendChild(loadingEl);
            } else {
                  document.getElementById('loading').remove(); // exemplo de como deletar o elemento loading!!!
            }
      }




# React Native


## Conceitos e Primeiros Passos




- Para criar um novo projeto:


    (Já na pasta onde o projeto deverá ser criado)
    Terminal > react-native init NomeDoProjeto
    Terminal > cd NomeDoProjeto
    Terminal > react-native run-ios
    (Ou react-native run-android)


- Arquivo explicando a montar o ambiente
- Estrutura de pastas:
      - __tests__ (onde ficam os arquivos de testes unitários)
      - android (arquivos nativos do android)
      - ios (arquivos nativos do iOS)
      - node_modules
      - index.js (arquivos de entrada da aplicação)
      - App.js (arquivo principal da aplicação)


- No arquivo App.js, devemos criar uma classe que extende a classe component do 'react'
- Obrigadtoriamente, toda classe que extende "Component" precisa ter o método "Render()".
      - Método render() retorna um conteúdo jsx
      - jsx é como se fosse um html/xml dentro do javascritpt:
            - <View> é como se fosse a <div> do html
            - <Text> é como se fosse um <span> do html


- Para auto reload do emulador:
      - No Android: ctrl + M
      - No iOS: cmd + D
      - No emulador também deve existir uma opção de "live reload"


- No React Native não existe herança de estilo


- O estilo do componente "ScrollView" é definido pela propriedade "contentContainerStyle", ao invés de apenas "style".




## Deixando Tudo Mais Bonito


- Estados e propriedades dos componentes


- Variaveis que são definidas dentro do objeto "state", quanto têm seu valor alterado, automaticamente faz com que o método "render()" seja chamado


- Criar uma nova pasta "components" para os outros componentes da aplicação




## Requisição à API e Storage


- Criar um novo componente para o modal


- O estado da classe ("state") nunca pode ser alterado diretamente; sempre modificamos ele através de um setState, e assim, todo seu conteúdo é retornado.


- O banco de dados interno do dispositivo nós acessamos através da classe "AsyncStorage"; com isso, podemos salvar os estados da aplicação na memória do dispositivo e não perdemos os dados a cada refresh ou quando fechamos e reabrimos o aplicativo






# Firebase


## Passos para configurar Authentication do Firebase com React Native


- seguinto o tutorial: https://www.youtube.com/watch?v=MxXyR0CN4v0


- Instalar o pacote firebase:


    Terminal > yarn add react-native-firebase


- Fazer a conexão do código nativo do firebase com android/ios:


    Terminal > react-native link react-native-firebase


- Abra o projeto:


    Terminal > react-native run-ios


- No ambiente do firebase, depois de criar um novo projeto, clicar em:
    
    - "Adicionar o Firebase ao seu aplicativo iOS"
    - Registrar um nome (ex.: com.healthinn.firebaseTest -> ou melhor: ver o nome da classe do projeto no xcode!!!)
    - Fazer download do "GoogleService-Info.plist"
    - Continuar e finalizar


- Abrir o projeto do firebase no xCode (ex.: para o projeto TestFirebase)


    - TestFirebase > ios > TestFirebase.xcodeproj
    - Jogar na pasta "TestFirebase" dentro do projeto xCode o arquivo que acabamos de baixar
    - Selecionar "Copy items if needed"


- Voltando ao ambiente react:


    - Abrir a o arquivo "AppDelegate.m" dentro da pasta ios
    (shortcut no VSCode: cmd + P)
    - inserir o código:


        #import <Firebase.h>


        ...
        // e abaixo do código jsCodeLocation, inserir:


        [FIRApp configure];


- No terminal, entrar na pasta ios para configurar o CocoaPods (gerenciador de pacotes para o ios)


    (antes tive que fazer o download do SDK do cocoapods para o comando pod funcionar!)
    Terminal > cd ios
    Terminal > pod init


- No VSCode, abrir o arquivo Podfile, criado no step anteior:


    - Remover o seguinte código:


          target 'TestFirebase-tvOSTests' do
            inherit! :search_paths
            # Pods for testing
          end


    -  Descomentar o " # platform :ios, '9.0' ":


        platform :ios, '9.0'


    - Adicionar alterações no projeto xCode:


        - no projeto principal, clicar no menu para mostrar os targets;
        - em cada target, ir na tab "build settings" e procurar por "other linker flags"
        - Verificar se tem a opção "$(inherited)"; se não tiver, adicionar


    - Na pasta ios, rodar o comando:


        Terminal > pod install


    - No arquivo Podfile, adicionar a dependência do Firebase:


        ...
        // abaixo da linha # Pods for TestFirebase:


        pod 'Firebase/Core'


    - Na pasta ios, rodar:


        Terminal > pod update


    - Depois que fizemos o pod install, o arquivo "TestFirebase.xcworkspace" foi criado; agora, sempre que formos acessar o projeto pelo xcode, entraremos por esse arquivo, e não pelo que utilizamos antes (o "TestFirebase.xcodeproj")


- Agora, para conectar com o Android:


    - abrir o projeto firebase no site e clicar em "adicionar outro app"
    - para o nome do projeto, tem que estar igual ao definido no arquivo "AndroidManifes.xml":


        package="com.testfirebase"
        (no caso, inserir "com.testfirebase" no nome)


    - Baixar o arquivo "google-services.json"
    - continuar e finalizar


    - Copiar esse arquivo que acabamos de baixar para a pasta "android > app" do projeto


    - No visual studio code, dentro da pasta android:


        - abrir o arquivo "build.gradle" da raiz da pasta androis (não o de dentro da pasta "app")
        - abaixo das dependencies, adicionar


            classpath 'com.google.gms:google-services:3.1.2'
            (para isso funcionar, no emulador tem que ter o google play instalado e atualizado)


        - agora, dentro da pasta "app", abrir o outro arquivo "build.gradle", e no final de tudo, adicionar:


            apply plugin: 'com.google.gms.google-services'


            ...
            // um pouco acima, na parte das dependencias, adicionar:


            // Firebase dependencies
            compile "com.google.android.gms:play-services-base:11.6.0"
            compile "com.google.firebase:firebase-core:11.6.0"


        - agora, voltando no primeiro arquivo "build.gradle", fora da pasta "app":


            ...
            // dentro de "allprojects { repositories {", adicionar um novo "maven":


            maven {
                url 'https://maven.google.com/'
            }


            (no meu já tinha esse maven criado…)


    - Quando da erro no build, mudar essa linha abaixo do arquivo “android > gradle > wrapper > gradle-wrapper.properties"
        
        distributionUrl=https\://services.gradle.org/distributions/gradle-4.1-all.zip




## Instalação do pacote de autenticação:


- No ios, dentro do arquivo Podfile, adicionar:


    // abaixo da linha " pod 'Firebase/Core' ":


        pod 'Firebase/Auth'


    - depois, rodar o comando na pasta ios:


    Terminal > pod update


- No Android, são apenas alguns passos a mais:


    - dentro do arquivo "build.gradle" de dentro da pasta app:


    ...
    // nas dependencias, onde adicionamos o firebase-core, adicionar a nova dependência:


    compile "com.google.firebase:firebase-auth:11.6.0"


    - abrir o arquivo "MainApplication.java", dentro da pasta "Android > app > src > main > com > testfirebase" (no caso desse projeto):


    ...
    // abaixo do "import io.invertase.firebase.RNFirebasePackage;", adicionar:


    import io.invertase.firebase.auth.RNFirebaseAuthPackage;


    ...
    // depois, abaixo de "new RNFirebasePackage()", adicionar novo projeto (não esquecer da vírgula!!!):


    new RNFirebasePackage(), // adicionar essa vírgula
    new RNFirebaseAuthPackage()


## Configurar método de login no Firebase


- Na plataforma Firebase, entrar no item "Authentication" e clicar em "configurar método de login"
- Para esse exemplo, selecionar "email/senha" > ativar > salvar
- volar na tab "usuários" e adicionar um novo usuário/senha exemplo


## Alguns problemas que encontrei e suas soluções:


- Depois de adicionar o Firebase/Database, ao rodar o comando “firebase.database().ref()” dá erro no simulador!
    -> Solução: fecha o simulador (e o terminal do simulador) e, no terminal, roda um “pod update” dentro da pasta iOS e um “react-native run-ios” na pasta do projeto para reiniciar o simulador.






