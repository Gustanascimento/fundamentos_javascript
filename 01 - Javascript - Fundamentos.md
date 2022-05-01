# Javascript - Fundamentos

### Organização Básica

{

bloco de códigos (chaves)

(dentro desses blocos, sentenças de código)

{

sentenças 2

}

}

### Comentários

```jsx
//Comentário](//comentário) de linha

/*
*
* Comentário de 
* múltiplas linhas
*
*/
```

### Constantes e Variáveis

var a = 3  *(var(identificador de variável global) rotulo = valor) - variável é anexada à janela!*

let b = 4  *(let(identificador de variável local)  rotulo = valor) - valor mutável*

const c = 5 *(const(identificador de constante)  rotulo = valor)  - valor não muda*

### **Tipos de Dados**

```jsx
console.log(typeof qualquer)
console.log(Numer.isInteger(numero_a_verificar_se_é_inteiro))
```

1 - **NUMBER - Valores numéricos**

1.1 - **Int e Float:** 

const peso1 = 1

const peso2 = Number( '2.0' )

toFixed(2) - arredonda float em 2 casas decimais

1.2 - Obs: 

Dividir um número por 0 retorna Infinity

Dividir uma string de um numero inteiro por um valor: "10"/2 = 5

Nan - Not a Number

1.3 - Conversão

Numero p/ string: concatenar com "" —> 1 + "" = "1"

String p/ numero: Number( '2' ) = 2

'3'+2 = 32

1.4 - MATH 

Math.PI = pi

Math.pow(base, elevação) ou base ** elevação

2 - STRING

const cidade = "Recife"

cidade.charAt(4) - Valor presente no indice 4 da string

cidadecharCodeAt(3) - Valor do char na tabela ASCII

cidade.indexOf('c') - Indice do char na string

cidade.substring(1) - String a partir do indice

cidade.substring(0,3) - String do indice 0 até 3

'Cidade'.concat(cidade).concat('!")

'Cidade' + cidade + '!"

cidade.replace(char 1, char 2) - Substitui caractere 1 pelo 2

char 1 pode ser: \d/ ou \w/

'Joao, Maria, Pedro' . split ( , ) - Cria array a partir de string

```jsx
nome = Mundo
quant = 2

console.log(`Olá ${nome}`)

console.log('Olá %s! Já mandei isso %i vezes', nome, quant)

console.log('%c Big message', 'font-size: 36px; font-weight: bold')

console.log ('Nome = ', nome)
```

3 - BOOLEAN

let falso = false

let verdadeiro = true

verdadeiro = 1 //true

false = !true

true = !false

Todos se comportam como verdadeiro:

Inteiros positivos e negativos (exceto o zero)

String não vazia (" "), ("Teste")

Lista

!!Infinity

Se comportam como falso:

!!0

String Vazia (!!'')

!!null

!!NaN (not a number)

!!undefined

|| - OU —>

console.log ("|| null || 0 || Nan) = false

console.log("" || undefined || " ") = true

Iniciar uma variável vazia. caso ela seja alterada, imprimir o valor. caso não seja, imprimir um valor padrão:

```jsx
let nome = ''
console.log(nome || 'Não informado')

output: 'Não informado'
```

```jsx
let nome = 'Gustavo'
console.log(nome || 'Não informado')

output: 'Gustavo'
```

4 - ARRAY (Vetor, Lista)

Estrutura indexada. Acessar elementos pelo index:

```jsx
const valores = [7.1, 3.2, 5.3, 6.8, 1.3]

console.log(valores[0],valores[3])
-- 7.1 6.8

//Caso seja inserido um index não existente: retorna undefined

//Também é possível acessar via Destructuring
```

Exibir todo o array:

```jsx
console.log(valores)
```

Exibir tamanho do array:

```jsx
console.log(valores.length)
```

Adicionar elementos no array:

```jsx
valores.push(false, null, 'teste', {id:3}, 33.4)
```

Remover elemento:

```jsx
console.log(valores.pop()) //remove último valor inserido

delete valores[indice] //remove elemento do indice informado
```

5 - OBJECT

Criação de um objeto atribuindo valores:

```jsx
const objeto = {}  //par chave:valor
objeto.chave1 = 'Valor da chave 1'
objeto.chave2 = 'Valor da chave 2'

class celular = {}
celular.nome = 'Galaxy S10 Lite 128GB'
celular.preco = 1927,00
celular.desconto = 0.40

console.log(celular)
```

Criação literal de um objeto:

```jsx
const celular2 = {
		nome: 'Galaxy S9 Plus',
		preco: 1899,90,
		desconto: 0.05
}

console.log(celular2)
console.log(celular2.nome)

//Também é possível acessar via Destructuring

const celular3 = {nome:'Mi Note 10 Lite', preco: 1724,99}
```

Objetos aninhados:

```jsx
const cliente = {
		nome: 'Gustavo',
		idade: 22,
		peso: 71.2,
		endereco: {
			logradouro: 'Rua Leonor Soares Pessoa',
			numero: 57,
			complemento: 'Apto 1002'
		}
}
```

Criação de objeto com valor genérico usando o this:

```jsx
function Obj(nome) {
	this.nome = nome
	this.funcao = function() {
		//executa instruções dessa funcao	
	}
}

const MeuObjeto1 = new Obj('Cadeira')
const MeuObjeto2 = new Obj('Mesa')

console.log(MeuObjeto1.nome)
console.log(MeuObjeto2.nome)
//mesa
//cadeira

console.log(MeuObjeto1.funcao)
```

### Null e Undefined

```jsx
let valor = null //variável valor não aponta para nenhum endereço de memória

delete celular.valor
celular.valor = null //zerar uma referência de valor para a variavel

```

```jsx
console.log(valor2) //Erro not defined
let valor2
console.log(valor) //Undefined - variável não declarada

console.log(celular2.cor) //undefined dentro de objeto
```

# Funções

Verbo; ação; **bloco** de instruções; trecho

Função sem retorno:

```jsx
function imprimirSoma(a, b) {
	c = a + b
	console.log(c)
}

imprimirSoma(2, 3)
imprimirSoma(2) //Saída: NaN
imprimirSoma() //Saída: NaM
imprimirSoma(10, 5, 4, 8, 6) //Pega apenas os dois primeiros parâmetros    
```

Função com retorno:

```jsx
function soma(a, b):
	c = a + b
	return c

console.log(soma(2,3))
```

Armazenando uma Função em uma variável

```jsx
const imprimirSoma = function (a, b) {
	console.log(a+b)
}

imprimirSoma(2, 3)
```

Armazenando função "Arrow" em uma variável

```jsx
const soma = (a, b) => {return a + b}
console.log(soma(2, 3))

const resultado = media => media >= 7 ? 'Aprovado' : 'Reprovado'
console.log(resultado(7.1))

//exemplo acima é igual abaixo
const resultado = media => {
	return media >= 7 ? 'Aprovado' : 'Reprovado'
}
console.log(resultado(7.1))
```

Função com retorno implícito (Função compacta)

```jsx
const subtracao = (a, b) => a - b  //Retorna implicitamente a-b
console.log(subtracao(2, 3))
```

## Laços de Repetição (apenas um spoiler)

FOR

```jsx
for (var i = 0; i<10, i++) {  //for com var. o i pode ser acessado depois
	console.log(i)
}

for (let i = 0; i<10, i++) {  //for com let. o i fica não defined após o fim do loop
	console.log(i)
}
```

## Operadores

1. ATRIBUIÇÃO (=)
    
    ```jsx
    const a = 7
    let b = 7
    
    b += a //Atribuição aditiva        --> b = b + a
    b -= a //Atribuição subtrativa     --> b = b - a
    b *= 2 //Atribuição multiplicativa --> b = b * 2
    b /= 2 //Atribuição divisiva       --> b = b/2
    b % 2  //Atribuição modular        --> b = b mod 2 (resto da divisao)
    ```
    
2. DESTRUCTURING
    
    Acessar elementos de um objeto e atribuir a variáveis distintas (com destructuring):
    
    ```jsx
    const estudante = {
    		nome: 'Gustavo',
    		idade: 22,
    		peso: 70.1,
    		endereco: {
    			logradouro: 'Rua Leonor Soares Pessoa',
    			numero: 57,
    			complemento: 'Apto 1002'
    		}
    }
    
    const {nome, idade} = estudante  //Retire do objeto pessoa os atributos nome e idade
    console.log(nome, idade)
    
    const {nome: n, idade: x} = estudante  //Retire do objeto pessoa os atributos nome e idade
    																		// e salve esses atributos em duas novas variáveis
    console.log(n, x)
    
    const {nome = 'Não definido'} = estudante //Caso o parametro nao tenha sido declarado dentro do objeto
    																					// vai retornar o valor padrão. Caso tenha sido, retorna o 
    																					// valor declarado.
    
    const {endereco: {logradouro, numero, cep}} = estudante  //Acessando dados aninhados
    console.log(logradouro, numero, cep)
    
    const {logradouro, numero, cep} = estudante.endereco  //Acessando dados aninhados diretamente
    console.log(logradouro, numero, cep)
    ```
    
    Retirar elementos de um array e atribuir a variáveis distintas (com destructuring):
    
    ```jsx
    array1 = [20]
    const [a] = array
    console.log(a) //20
    
    array2 = [10, 7, 9, 8]
    const [n1, , n3, ,n5, n6] = array2
    console.log(n1,n3,n5,n6) //10, 7, 9, 8
    
    matriz = [[0, 9, 8], [9, 6, 8]]
    const [, [,nota]] = matriz           //Pouco utilizado
    console.log(nota) //6
    ```
    
    Utilizar o destructuring com um objeto como parâmetro para uma função:
    
    ```jsx
    function apresentar({nome, idade}) {
        console.log('Olá, me chamo ' + nome + ' e tenho '+ idade + ' anos');
    }
     
    const pessoa = {nome: 'Fulano', idade: '22', sexo: 'M', profissao: 'Dev'}
     
    apresentar(pessoa)
    
    //EXEMPLO ACIMA CASO FOSSE SEM DESTRUCTURING:
    
    function apresentar(pessoa) {
        const nome = pessoa.nome
        const idade = pessoa.idade
        console.log('Olá, me chamo ' + nome + 'e tenho '+ idade + ' anos');
    }
     
    const pessoa = {nome: 'Fulano', idade: '22', sexo: 'M', profissao: 'Dev'}
     
    apresentar(pessoa)
    ```
    
    Utilizar o destructuring com um array como parâmetro para uma função:
    
    ```jsx
    function apresentar([nome, idade]) {
        console.log('Olá, me chamo ' + nome + ' e tenho '+ idade + ' anos');
    }
     
    const pessoa = ['Fulano','22','M', 'Dev']
    apresentar(pessoa)
    
    //EXEMPLO ACIMA CASO FOSSE SEM DESTRUCTURING:
    
    function apresentar(pessoa) {
        const nome = pessoa[0]
        const idade = pessoa[1]
        console.log('Olá, me chamo ' + nome + ' e tenho '+ idade + ' anos');
    }
     
    const pessoa = ['Fulano','22','M', 'Dev']
    apresentar(pessoa)
    ```
    
3. ARITMÉTICOS
    
    ```jsx
    + soma
    - subtração
    * multiplicação
    / divisão
    % resto da divisão
    ** potenciação    //Raiz quadrana num ** (1/2)
    ```
    
4. RELACIONAIS (retorna um booleano)
    
    ```jsx
    == é igual?   (ignora o tipo)
    === é igual no valor e tipo?
    != é diferente?    (ignora o tipo)
    !== é diferente no valor e tipo?
    
    < menor que
    > maior que
    <= menor ou igual
    >= maior ou igual
    
    undefined == null  //true
    undefined === null //false
    ```
    
5. LÓGICOS (tabela verdade)
    
    ```jsx
    ||  ou
    &&  e
    != (ou exclusivo)  //ex: const verdadeoufalso = const1 != const2
    ```
    
6. UNÁRIOS
    
    ```jsx
    num1++   //incrementa em 1
    num1--   //decrementa em 1
    ```
    
7. TERNÁRIOS
    
    ```jsx
    const nota = 7.4
    
    nota >= 7 ? 'Aprovado' : 'Reprovado'
    
    //modelo: valor condicao objetivo ? 'true' : 'false'
    valor_a_ser_verificado >= objetivo ? 'String retornada caso verdadeiro' : 'String Retornada caso falso' 
    ```
    

### Tratamento de Erro

```jsx
function tratarErroeLancar(erro) {
    //throw new Error('Erro!!! Entrar em contato com o suporte')
    //throw 10
    //throw true
    //throw 'mensagem de erro'
		console.log(erro)
}

function funcao(parametros){
    try{  //Vai primeiro tentar executar essa parte
        console.log(parametros)
    }
    catch(e){ //Caso dê erro, executa essa parte
        tratarErroeLancar(e)
    }
    finally{ //Por fim, executa essa após um erro ou não
        console.log('Final')
    }
}

parametro = '10'
valorAleatorio = funcao(parametro)
```