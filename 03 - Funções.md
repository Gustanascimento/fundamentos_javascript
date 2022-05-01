# Funções

Funções podem ser criadas de forma literal (padrão), 

### First-Class Object / Cidadão de Primeira Linha

Função pode ser tratada como um dado (podem ser passadas como parâmetro, podem ser retornadas de funções, podem ser criadas dentro de outras funções, armazenar uma função numa variável...)

### Declaração de Forma Literal (function declaration)

Pode ou não receber parâmetros e pode ou não retornar valores

```jsx
function func1(parâmetros){
	//bloco/sentença de códigos
}
```

### Armazenar Função em Variável

```jsx
const func2 = function() { }
```

### Armazenar Função em Array

```jsx
const array = [function(a,b) {return a+b}, func1, func2]

console.log(array[0](2, 3))  //5
```

### Armazenar Função em Objetos

```jsx
const obj = {}

obj.falar = function() {return 'Olá!'}
console.log(obj.falar())
```

### Passar Função como parâmetro para outra Função

```jsx
function func1(func2){
		func2()
}

func1(function() {//executa aqui }) //passando uma funcao como parametro para func1
```

### Função Retorna Função

```jsx
function soma(a, b){
		return function(c){
				console.log(a + b + c)
		}
}

soma(2, 3)(4)
```

### Diferentes formas de declarar funções

```jsx
console.log(soma(3, 4))

// function declaration
// O interpretador do Javascript lê primeiro todas as funções antes de executar os script em si, por isso a função soma no function declaration pode ser usada antes mesmo de ser declarada oficialmente
function soma(x, y) {
    return x + y
}
```

```jsx
console.log(sub(3, 4)) //error: sub is not defined
// function expression
const sub = function (x, y) {
    return x - y
}
console.log(sub(3, 4)) //-1

// named function expression
const mult = function mult(x, y) {
    return x * y
}
console.log(mult(3, 4))
```

### Arguments (Funções com Parâmetros Variáveis)

```jsx
function imprimeArgumentos(){
		console.log(arguments) //[Arguments] { '0': 2, '1': 5, '2': 3, '3': 4 } 
		for (x in arguments){ 
			console.log(arguments[x])
	}
}
imprimeArgumentos(2,5,3,4)

//Exemplo de arguments com soma:
function soma() {
	let soma = 0
	for (x in arguments){  // arguments = array interno da função com todo os argumentos
			soma+= arguments[x]
	}
	console.log(soma)
}

soma(2.9,5.5,3.7,4.8) // 14
```

- Pode passar números para serem somados ou strings para serem concatenadas
- Caso seja passado um number e uma string, e seja utilizado a concatenação com arguments, tudo será concatenado.

### Parâmetro Padrão

Valor padrão considerado pela função para uma variável quando nenhum valor foi atribuído 

```jsx
function soma(a=1, b=1, c=1){
		return a + b + c
}

soma(1, 2, 3)
```

- Para garantir que o valor passado (caso não seja um number) não dê erro:
    
    Estratégia 1 para valor padrão
    
    ```jsx
    function soma(a, b, c){
    		a = a || 1
    		b = b || 1
    		c = c || 1		
    
    		return a + b + c
    }
    console.log(soma(1, 2, 3))
    
    // essa estatégia não funciona para valores == 0
    // útil para uma variável que recebe uma string. caso nulo, coloca valor padrão.
    // ex: usuário não logado, exibe User: "Anônimo"
    
    //também utilizado para variáveis criadas dentro da função
    ```
    
    Estratégia operador ternário com isNan para valor padrão 1
    
    ```jsx
    function soma(a, b, c){
    		a  = isNaN(a) ? 1 : a //se não for um número, adota o valor padrão 1. caso seja, continua com o valor atribuído
    		b  = isNaN(b) ? 1 : b
    		c  = isNaN(c) ? 1 : c
    		return a + b + c
    }
    console.log(soma(1, 2, 3))
    ```
    

### THIS (self)

Objeto que está sendo referenciado num contexto de execução. Acessar atributos de um objeto. 

No JavaScript, entretanto, esse THIS pode variar de acordo com quem o chamou:

```jsx
console.log(this === window)  //true no caso do navegador

function f1() { console.log(this === window)}
document.getElementsByTagName('body')[0].onclick = f1
// ao clicar na página, a função f1 é executada (retorna false)

const f2 = () => console.log(this === window)
document.getElementsByTagName('body')[0].onclick = f2
// ao clicar na página, a função arrow f2 é executada (retorna true)
// F2 foi criada no escopo global

// O this pode variar representando a window, um objeto ou o elemento a ser clicado
// Utilizando uma função arrow ele não varia 
```

BIND (Fazer referência a um objeto para a execução do método)

```jsx
const pessoa = {
		saudacao : 'Bom Dia!!!',
		falar() {
				console.log(this.saudacao)
		}
}

pessoa.falar()  //imprime bom dia sem problemas

const falar = pessoa.falar
falar() //undefined. o this é ligado à constante falar

const falar2 = pessoa.falar.bind(pessoa)
falar2() //imprime bom dia sem problemas
```

Atribuindo o this para uma outra variável antes de executar a função:

```jsx
function Pessoa(){
		this.idade = 20

		const selffff = this

	setInterval(function() {
								self.idade++
								console.log(selffff.idade)
							},1000) 
		//a cada x milissegundos, essa função passada para o setInterval será executada
}
// Quem está "disparando" essa função é o timer do setInterval,
// não fomos nós quem passamos os atributos via parenteses
new Pessoa
```

# Funções Arrow

- Simplificar sintaxe de pequenas funções específicas
- Possuem retorno implícito
- Não possui necessidade de criar bloco

```jsx
let dobro = funcion(a) {    //Função Padrão
		return 2 * a
}

dobro = (a) => {     //Função arrow com bloco
		return 2 * a
}

dobro = a => 2 * a    //Função arrow sem bloco e com retorno implícito  
```

- O This dentro de uma função arrow é fixo
    - [O fato de ele ser chamado por outras funções não influencia]

```jsx
function Pessoa() {
		this.idade = 0

setInterval (() => {
				this.idade++
				console.log(this.idade)  //This aponta para pessoa
		}, 1000)
}

new Pessoa
```

- Porém

```jsx
let comparaComThis = function (param) {
		console.log(this === param)
}

comparaComThis(global) //no caso do NodeJS - true
comparaComThis(window) //no caso do navegador - true

const obj = {}
comparaComThis = comparaComThis.bind(obj)

let comparaComThis = function (param) {
		console.log(this === param)
}
```

## Funções Anônimas

Funções sem nome

- Uma arrow function é sempre uma função anônima

```jsx
const soma = function (x, y) {
		return x + y
}

const imprimirResultado = function (a, b, operacao = soma) {
		console.log(operacao(a, b))
}
```

```jsx
imprimirResultado(3, 4) //7
imprimirResultado(3, 4, soma) //7
imprimirResultado(3, 4, function (x, y) {
		return x - y
}) //-1
imprimirResultado(3, 4, (x, y) => x * y) //12
```

- Funções dentro de objetos (métodos) também são funções anônimas

# Funções de Callback

***Passar função para outra função e quando determinado evento ocorrer, a função que foi passada vai ser chamada de volta***

**Exemplo de evento:**

- Evento: Loop percorrendo cada elemento que um array possui
    - Chama o callback passando o próprio elemento e o índice
    - Encontrou um novo elemento = novo evento = chama novamente callback

Em código:

### Imprimir elementos de array com função de callback

```jsx
const fabricantes = ['mercedes', 'marcopolo', 'toyota', 'renault']

function imprimir(nome, indice) {
		console.log(`${indice+1}. ${nome}`)
}

fabricantes.forEach(imprimir)
```

```jsx
fabricantes.forEach(function(a){console.log(a)})
```

Com retorno implícito e função arrow:

```jsx
fabricantes.forEach(a => console.log(a))
```

## Outros Exemplos de utilização de função Callback:

### Copiar determinados valores de um array em outro array

```jsx
const notas = [7.7, 6.5, 5.2, 8.9, 3.6, 7.1, 9.0]
```

- Sem callback

```jsx
let notasBaixas = []

for (let i in notas) {
		if (notas[i] < 7) {
				notasBaixas.push(notas[i])
		}
}

console.log(notasBaixas)
```

- Com callback

```jsx
const notasBaixas2 = notas.filter(function (nota) {
		return nota < 7
})

console.log(notasBaixas2)
```

```jsx
// Utilizando arrow

const notasBaixas3 = notas.filter(nota => nota < 7)
console.log(notasBaixas3)
```

```jsx
// Salvando a função numa variável para ela ser reutilizada em outros locais

const notasMenorQue7 = nota => nota < 7

const notasBaixas4 = notas.filter(notasMenorQue7)
console.log(notasBaixas4)
```

### Callback no Browser

```jsx
document.getElementsByTagName('body')[0].onclick = function (e) {
    console.log('O evento ocorreu!')
}
```

# Closures

- Contexto Léxico
    
    A função carrega consigo o contexto/escopo em que ela foi definida
    
    ```jsx
    const valor = 'Global'
    
    function minhaFuncao() {
        console.log(valor)
    }
    
    function exec() {
        const valor = 'Local'
        minhaFuncao()
    }
    
    exec() //Global
    
    // A função exec() chamada vai buscar o valor no contexto em que ela foi declarada (global)
    ```
    

- Closure é o escopo (closure/envolvimento/fechamento) criado quando uma função é declarada
- Esse escopo permite a função acessar e manipular variáveis externas à função

```jsx
// Contexto léxico em ação!
const x = 'Global'

function fora() {
		const x = 'Local'
		function dentro() {
				return x
		}
		return dentro
}

const minhaFuncao = fora()
console.log(minhaFuncao()) //Local

//a função dentro() foi declarada na função fora()
//então o retorno vai ser buscado no contexo da função em que ela foi declarada
///ou seja: Local
```

# Funções Construtoras

- Orientação a Objetos

Funções que servem como um molde para a criação de objetos

Em outras linguagens: Classe e orientação a objetos

Ex:

```jsx
function Carro(velocidadeMaxima = 200, delta = 5) {
    // atributo privado
    let velocidadeAtual = 0

    // metodo publico
    this.acelerar = function () {
        if (velocidadeAtual + delta <= velocidadeMaxima) {
            velocidadeAtual += delta
        } else {
            velocidadeAtual = velocidadeMaxima
        }
    }

    // metodo publico
    this.getVelocidadeAtual = function () {
        return velocidadeAtual
    }
}
```

Criando um objeto:

```jsx
const ferrari = new Carro(350, 20)
ferrari.acelerar()
ferrari.acelerar()
ferrari.acelerar()
console.log(ferrari.getVelocidadeAtual())
```

```jsx
console.log(typeof Carro)   //function
console.log(typeof ferrari)  //object

```

# Funções Factory

Função que retorna um Objeto

```jsx
// Factory simples
function criarPessoa() { //parametros fixos
    return {
        nome: 'Ana',
        sobrenome: 'Silva'
    }
}

console.log(criarPessoa())
```

A função criarPessoa() vai estar sempre retornando um objeto mesmo sem a utilização do operador “new”. O fato de estar sendo utilizada a notação literal de objetos, uma nova instância independete do objeto é criado sempre na chamada dessa função

```jsx
function criarProduto(nome, preco) { //parametros variaveis
    return {
        nome,
        preco,
        desconto: 0.1
    }
}

console.log(criarProduto('Notebook', 2199.49))
console.log(criarProduto('iPad', 1199.49))
```

```jsx
function criarProduto(nome, preco) {
		return {
			nome: nome,
			preco: preco,
			desconto: 0.1
		}
}

console.log(criarProduto('Notebook', 2199.49))
console.log(criarProduto('iPad', 1199.49))

```

- Pode inserir ou não a atribuição dos parâmetros

## **Classes vs Funções Factory vs Funções Construtoras**

- **Classe**

```jsx
class Pessoa {
    constructor(nome) {
        this.nome = nome
    }

    falar() {
        console.log(`Meu nome é ${this.nome}`)
    }
}

const p1 = new Pessoa('João')
p1.falar()  //Meu nome é João
```

Porém, dependendo do contexto em que p1 é chamada, o nome pode ser undefined (como o onClick, por exemplo)

- **Função Factory**

```jsx
const criarPessoa = nome => {
    return {
        falar: () => console.log(`Meu nome é ${nome}`)
    }
}

const p2 = criarPessoa('João')
p2.falar() //Meu nome é João
```

Independente do contexto, p2 sempre vai ter o nome João (ou até que seja trocado)

- Função Construtora

```jsx
function Pessoa(nome) {
    this.nome = nome

    this.falar = function () {
        console.log(`Meu nome é ${this.nome}`)
    }
}

const p3 = new Pessoa('João')
p3.falar()  //Meu nome é João
console.log(p3.nome)  //João
```

Independente do contexto, p3 sempre vai ter o nome João (ou até que seja trocado)

- Função Construtora (com atributos não variáveis)

```jsx
function Pessoa(nome) {
    this.falar = function () {
        console.log(`Meu nome é ${nome}`)
    }
}

const p4 = new Pessoa('João')
p4.falar() //Meu nome é João
console.log(p4.nome) //Undefined
```

Independente do contexto, p4 sempre vai ter o nome João

# Função Auto Invocada (IIFE)

Quando estamos no escopo Global mas queremos fugir dele, utilizando tudo o que está dentro do escopo local, evitando a editar algo no escopo global (principalmente no caso do browser)

```jsx
// IIFE -> Immediately Invoked Function Expression

(function() {
    console.log('Será executado na hora!')
    console.log('Foge do escopo mais abrangente!')
})()
```

- Função é invocada imediatamente na hora em que é definida

# Call vs Apply

```jsx
function getPreco(imposto = 0, moeda = 'R$') {
    return `${moeda} ${this.preco * (1 - this.desc) * (1 + imposto)}`
}

const produto = {
    nome: 'Notebook',
    preco: 4589,
    desc: 0.15,
    getPreco
}

global.preco = 20
global.desc = 0.1
console.log(getPreco()) //R$ 18
console.log(produto.getPreco()) //R$3900.65
```

```jsx
const carro = { preco: 49990, desc: 0.20 }

console.log(getPreco.call(carro))  //R$ 39992
console.log(getPreco.apply(carro)) //R$ 39992

console.log(getPreco.call(carro, 0.17, '$')) //$ 46790.64
console.log(getPreco.apply(global, [0.17, '$'])) //$ 46790.64
```

A única diferença é a maneira de passar os parâmetros!

O Apply espera sempre um objeto [array]

O Call pode passar valores individuais