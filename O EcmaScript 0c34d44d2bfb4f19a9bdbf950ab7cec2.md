# O EcmaScript

## **O que é ECMA?**

ECMA é uma organização europeia focada em padronização de sistemas de informação. 

Ela é responsável por manter e atualizar um conjunto de regras e especificações chamado ECMAScript.

## Diferença entre ECMAScript e JavaScript

O **ECMAScript** conforme falado acima, é como se fosse um “conjunto de regras”, são especificações criadas pela empresa ECMA que o **JavaScript** segue a risca desde o ES3 em 1999. **JavaScript** é a implementação mais concreta destas regras. 

Existem outras linguagens, como o ActionScript, que se baseiam no **ECMAScript**  mas o **JS** é o mais fiel e vai se atualizando confome o **ECMAScript** se atualiza fazendo com que o padrão de código se mantenha de acordo com as normas da ECMA.

## Principais mudanças que ocorreram com o ES6

- Classes
    - As classes em JavaScript foram introduzidas somente após o ES6 e são a forma mais rápida de criar objetos.
    Basicamente, programadores de outras linguagens como PHP, Python, Java tinham uma reclamação no que se tratava de criação de classes em JS e toda essa movimentação fez com que em 2015 fosse implementada uma forma de se criar classes de forma organizada.
        
        ```jsx
        class Animal {
          constructor(name, sound) {
            this.name = name;
            this.sound = sound;
          }
        
          speak(){
            console.log(`${this.name} fala: "${this.sound}"`);
          }
        }
        
        class Dog extends Animal { 
          constructor(name, breed) {        
            super(name, "auuuuu");          
            this.breed = breed;           
          }
        }
        
        class Cat extends Animal {    // herança
          constructor(name, breed) {  // método construtor definimos os métodos que precisam para criar a classe
            super(name, "miaaaw");    // herdando o nome que vem da classe Animal
            this.breed = breed;       // Dentro de animal, é um cachorro então defina raça      
          }
        }
        
        const faiska = new Dog("Faiska", "Golden Retriever");
        const milk = new Cat("Milk", "Sphynx");
        faiska.speak(); // Output: "faiskafala: "auuuu""
        milk.speak() // Output: "Milk fala: "miaaaw""
        
        ```
        
        - Forma antiga de se declarar classes
            
            ![Untitled](O%20EcmaScript%200c34d44d2bfb4f19a9bdbf950ab7cec2/Untitled.png)
            
            Perceba como a sintaxe era bem mais suja. E é por isso que somente agora a OO vem se popularizando no JavaScript
            
        
    
- Arrow Functions
    
    A arrow facilitou demais o desenvolvimento pelo motivo de que são mais curtas e mais legíveis / fáceis de se interpretar e isso aumenta a sua eficiência como programador em termos de produção e também a eficiência do codigo que fica mais fácil de ser interpretado/lido. 
    
    Abaixo 3 exemplos de como declarar uma arrow function:
    
    ```jsx
    (param1) => {
      // código da função
      return result;
    };
    
    param => {
      // código da função
      return result;
    };
    
    param1 => result
    			 ou
    	  () => {}
    
    Se você não coloca parâmetro nenhum, é obrigado a informar com ()
    Você também pode usar mais de um parâmetro.
    ```
    
    - Modelo antigo parar declarar  funções anônimas
        
        ![Untitled](O%20EcmaScript%200c34d44d2bfb4f19a9bdbf950ab7cec2/Untitled%201.png)
        
        Esse modelo ainda é suportado, caso você queira declarar uma função anônima e salvar ela em uma variável para usar em outro lugar do código pode ser que seja uma boa ideia.
        
- Promises
    
    As Promises são algo recente no JavaScript e chegaram apenas com ES6. Elas são muito utilizadas para lidar com a programação assíncrona que era uma dificuldade no javascript,  requisições HTTP, processos de I/O e etc.
    
    As Promises possuem 3 estados: Pendente, Resolvida e Rejeitada
    
    - Neste primeiro exemplo temos uma requisição HTTP sendo feita de forma nativa.
        
        ```jsx
        fetch('https://apidadriven.com.br')
          .then(response => response.json())
          .then(data => console.log(data))
          .catch(error => console.error(error));
        
        ```
        
    - Neste segundo código, uma Promise sendo criada manualmente e simulando a assincronicidade. Então é criada uma Promise e quando ela for resolvida, se o resultado for > 0.5 cairá no resolve que passará o valor para o .then e só então será exibido no console.
        
        ```jsx
        const myPromise = new Promise((resolve, reject) => {
          const randomNum = Math.random();
          if (randomNum > 0.5) {
            resolve(randomNum);
          } else {
            reject(new Error('Random number was too low'));
          }
        });
        
        console.log('frase 1')
        myPromise
          .then(result => console.log(`Random number: ${result}`))
          .catch(error => console.error(error));
        console.log('frase 2')
        
        // output: 
        // frase 1
        // frase 2
        // resultado da promise
        ```
        
- Forma antiga de se fazer requisições HTTP
    
    Antes, para se ter programação assíncrona eram muito utilizados callbacks e a função setTimout. Abaixo um exemplo de requisição feita com a biblioteca xmlHttpRequests.
    
    Era muito mais difícil de manter e muito mais complexo também, uma vez que poderia gerar uma cadeia de callbacks gigantesca.
    
    ![Untitled](O%20EcmaScript%200c34d44d2bfb4f19a9bdbf950ab7cec2/Untitled%202.png)
    
- Template Strings / Template Literals
    
    São uma nova forma de construir expressões no meio das strings. Facilitam demais na hora de escrever código fazendo com que você não precisa ficar concatenando várias partes diferente. 
    Explicação direto ao ponto: Você pode utilizar variáveis junto com strings. 
    
    ```jsx
    const name = "Faiska";
    const temperature = 30;
    const message = `Eaí, ${name}! Que calor, hein? Hoje faz ${temperature}°.`;
    
    console.log(message); 
    // Output: "Eaí, Faiska! Que calor, hein? Hoje faz 30°.`"
    ```
    
    - forma antiga para se juntar expressões. Perceba como é mais poluído.
        
        ![Untitled](O%20EcmaScript%200c34d44d2bfb4f19a9bdbf950ab7cec2/Untitled%203.png)
        
- var let e const
    - var
        
        Com a chegada do ES6 virou uma má prática o uso de “var”. O grande problema que se viu é que quando você declara uma variável com ‘’var’’ ela tem problema de hoisting, ou seja, na hora da execução do código, é como se ela fosse levada para o topo do escopo e isso não gera erro, retorna undefined, o que pode causar bugs. Outro ponto é que ‘’var’’ tem escopo de função possibilitando que você sem querer substitua o valor dela ao longo do código.
        
        ```jsx
        // é como se acontecesse o seguinte:
        console.log(x); // undefined
        var x = 'filipe';
        
        // é o mesmo que : 
        var x;
        var y;
        console.log(x); // undefined
        console.log(y) // undefined
        x = 'filipe';
        y = 'leo'
        
        ```
        
    - let
        
        Essa foi uma das grandes novidades do ES6. Com a chegada dela, agora possuímos uma forma de declarar variáveis com escopo de bloco. O que significa que a variável declarada com “let” só poderá ser usada dentro do escopo que ela existe. Um ponto sobre variáveis declaradas com “let” é que elas podem ser alteradas ao longo do código então ainda é preciso ter cuidado com elas e usar em situações as quais você sabe que existe a possibilidade de alterá-las
        
        ```jsx
        let x = 5;
        
        if (true) {
          let x = 10;
          console.log(x); // 10
        }
        
        console.log(x); // 5
        ```
        
        ```jsx
        let x = 5;
        console.log(x); // 5
        x = 10;
        
        console.log(x); // 10
        ```
        
        Você pode declarar a variável com let sem atribuir um valor na hora, uma vez que o valor pode ser (re)atribuido ao longo do código
        
        ```jsx
        let x; // value: undefined
        ```
        
    - const
        
        Assim como “let”, variáveis declaradas com “const” também tem escopo de bloco, o que significa que a variável é acessível apenas dentro do bloco de código onde foi declarada. A grande diferença é que uma variável declarada com “const” não pode ter seu valor alterado.
        
        ```jsx
        const nome = 'faiska';
        
        console.log(nome); // faiska
        
        nome = 'haru'; // TypeError: Assignment to constant variable.
        ```
        
        Declarando uma variável com const, você também não pode deixar ela sem valor pois nao conseguirá alterar ao longo do código, então isso aqui retorna um erro:
        
        ```jsx
        let name;
        const name; // Uncaught SyntaxError: Missing initializer in const declaration;
        
        ```
        
- O que é Hoisting?
    
    O hoisting é um comportamento do JavaScript que leva as variáveis para o topo do escopo, seja o código ou a função, na hora da execução. O que faz com que ao tentar acessá-las mesmo não tendo sido declaradas, o retorno seja undefined e não um erro.
    
    O hoisting acontece com let e const também, entretanto a diferença é que mesmo que as variáveis declaradas com let e const sejam levadas para cima do escopo na hora da execução, o uso dela não está disponível até que a linha de código em que elas estão declaradas seja executada. Essa é a maior difernça entre estas duas e var.
    
    ```jsx
    "use strict"; 
    function imprimirNumero() {
      console.log(y); //undefined
      var y = 20;
    }
    
    imprimirNumero(); // undefined
    
    // é equivalente a 
    function imprimirNumero() {
      var y;
      console.log(y); // undefined
      y = 20;
    }
    
    imprimirNumero(); // undefined
    ```
    
    ```jsx
    "use strict";
    
    dfhosahfas
    fsdfoshfos
    fsuoffhsofhs
    ```
    
- strict mode
    
    O strict mode é ativado quando você declara “use strict” no começo do documento JS da sua aplicação ou quando você utiliza JavaScript module e é uma boa prática que você sempre use.
    
    Em resumo ele torna sua aplicação mais segura e previsível pois te priva de alguns erros básicos, uma vez que tem regras bem rigorosas. Segue alguns exemplos.
    
    - Impede a criação de variáveis globais sem intenção.
    - Impede você de usar palavras reservadas como nome de varíaveis.
    - Lembra do error de var? Pois é, com strict mode não é possível acessar variáveis não declaradas
    - Não é possível repetir nome de variáveis em um mesmo escopo
    
- Estruturas de dados
    - map
        
        Introduzido no ES6 o map é um método que possibilita a transformação de um array salvando em outro array sem alterar o original. Ele itera o array, passando item por item executando a função que você deseja e retorna um novo array com os ítens alterados.
        
        ```jsx
        const numbers = [1, 2, 3, 4, 5];
        
        const doubledNumbers = numbers.map(number => number * 2);
        
        console.log(doubledNumbers); // [2, 4, 6, 8, 10]
        ```
        
    - forEach
        
        Diferente do map, o forEach nos ajuda a manipular o array original, é um método que vai iterar por todo o array executando determinada função sobre aquele elemento.
        
        Ele pode receber alguns parametros mas os mais importantes são os 2 primeiros item e index
        
        ```jsx
        const numbers = [1, 2, 3, 4, 5];
        
        numbers.forEach(( item ) => {
        	console.log(item* 2)
        }); 
        
        Output: 
        // 2
        // 4
        // 6
        // 8
        // 10
        ```
        
        ```jsx
        const numbers = [1, 2, 3, 4, 5];
        
        numbers.forEach(( numero, index ) => {
        	console.log(numero * 2 , 'indice: ', index)
        }); 
        
        Output: 
        // 2 indice: 0
        // 4 indice: 1
        // 6 indice: 2
        // 8 indice: 3
        // 10 indice: 4
        ```
        
    - for e for of
        
        A estrutura for é um loop de repetição que permite que você execute funções repetidamente sem ter que ficar necessáriamente repetindo codigo/ação.
        
        Ela possui 3 parâmetros e é executada enquanto o segundo parâmetro for verdadeiro/ a condição for atendida. 
        Então a sintaxe básica do loop seria:
        
        ```jsx
        for (indice, condição, ação) {
        		código
        }
        ```
        
        Basicamente o que está acontecendo aqui é: Indice, verifica se a condição é verdadeira, se for, executa o código e a ação.
        
        Vamos ver um exemplo em que quero imprimir 10 números em sequência. 
        É importante ressaltar que os loops começam da posição que você definir no primeiro parâmetro, neste caso, 0.
        
        ```jsx
        for (let i = 0; i < 10; i++) {
          console.log(i);
        }
        // 0
        // 1
        // 2
        // 3
        // 4
        // 5
        // 6
        // 7
        // 8
        // 9
        ```
        
         
        
        O for of funciona como um loop normal, porém facilita muito a vida quando a única coisa que interessa a você é o valor que a lista tem em X índice, sendo assim, você acessa diretamente o valor naquele ponto. 
        Vamos para um exemplo:
        
        ```jsx
        Para acessar os valores de uma lista com um loop for normal 
        teriamos que fazer assim:
        const numbers = [1, 2, 3, 4, 5];
        
        for (let i = 0; i < numbers.length; i++) {
          console.log(numbers[i]);
        }
        
        Enquanto com for of você faz assim:
        
        const numbers = [1, 2, 3, 4, 5];
        
        for (const i of numbers) {
          console.log(i * 2); // 2 // 4 // 6 // 8
        
        }
        
        // 1
        // 2
        // 3
        // 4
        // 5
        ```
        
- Default Parameters
    
    Poder definir um valor como default no parametro de uma função nem sempre foi possível e isso tornava os códigos muito mais extensos, uma vez que precisavam ser feitas verificações dentro da função.  Basicamente o que acontece aqui é: Se você não definir um name ao executar a função, ela vai ser executada com ‘Faiska’, caso defina, será executada com o valor definido. Isso possibilita o uso de uma mesma função em vários momentos diferentes do código.
    
    ```jsx
    function dizerOla(name = 'Chewbaca') {
      console.log(`Oi, ${name}!`);
    }
    // Oi, Faiska!
    
    dizerOla('filipe'); // `Oi, Filipe!`
    
    dizerOla(); // `Oi, Chewbaca!`
    ```
    
    - Modo antigo de fazer isso:
        
        Perceba como o código fica maior já que você precisa atribuir um valor dentro da função
        
        ```jsx
        function dizerOla(name) {
          name = name || 'Chewbaca';
          console.log(`Hello, ${name}!`);
        }
        ```
        
    
- Destructuring
    
    Permite desestruturar arrays e objetos em variáveis mais facilmente e de forma acessível. Essa técnica normalmente é usada quando você vai precisar usar os valores salvos dentro dessa estrutura (array/objeto) em outras partes do código. 
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5];
    
    const [ first, second ] = numbers;
    
    console.log(first, second); // 1 2 
    ```
    
     É importante ressaltar que você poderia desestruturar a lista pegando todos os elementos de dentro dela, mas uma vez que você não faça isso e utilize somente alguns, a desestruturação funcionará por ordem, logo, first, second e third são os 3 primeiros itens do array numbers.
    
    Segue dois exemplos com objeto:
    
    ```jsx
    const person = { name: 'Rafael', age: 30, city: 'São Paulo' };
    const { name, age } = person;
    console.log(name, age); // Rafael 30
    
    console.log(name) //rafael
    console.log(person.name) // rafael
    ```
    
    ```jsx
    const person = { name: 'Rafael', 
    								  age: 30, 
    							     city: {
    												um: 'São Paulo', 
    												dois: 'Porto Alegre'
    										}
    							}
    const { name, city: { um: principalCity } } = person;
    console.log(principalCity); // São Paulo
    
    console.log(person.city.um) // sao paulo
    ```
    
    O que você deve se atentar nesse tipo de desestruturação é que caso você passe um valor inexistente o retorno será undefined.
    
    [https://github.com/FilipeTenedini/notion-repositories](https://github.com/FilipeTenedini/notion-repositories)