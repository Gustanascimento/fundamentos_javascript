# Estruturas de Controle e Repetição

### Condições

no caso de bool, tomar cuidado com o tipo da variável que está sendo avaliada pois uma string, por exemplo, pode retornar um true ou false

```jsx
nota >= 7
opcao !=-1

valor //valor é convertido para boolean 
() //false
null //false
undefined //false
NaN //false
'' //false
0 //false
-1 //true
' ' //true
'?' //true
[] //true
[1,2] //true
{} //true
```

**Exemplo: Retornar true ou false caso um número esteja entre um determinado intervalo**

```jsx
Number.prototype.entre = function (maior, menor) {
	return this >= menor && this <= maior
}

const valor = 8
console.log(valor.entre(10, 7)) //true
console.log(valor.entre(5, 2)) //false
```

### IF

```jsx
if (condição){
	//executar esse bloco
}
```

### IF/ELSE

```jsx
if (condição){
	//executar esse bloco caso condição verdadeira
}
else{
	//executa esse caso condicao falsa
}
```

### IF ELSE/IF (IF's encadeados)

```jsx
if (condição_1){
	//executar esse bloco caso condição1 verdadeira
}
else if (condicao_2){
	//executar esse bloco caso condição2 verdadeira
}
else if (condicao_3){
	//executar esse bloco caso condição3 verdadeira
}
else {
	//executa caso todas as outras condições sejam falsas
}
```

### SWITCH

```jsx
const valor = 8

switch(valor){
	case 10:
			//executa essa linha
			break
	
	case 9:
			//executa essa linha
			break

	case 8:	case 7: case 6: case 5: case 4:
			//executa essa linha
			break
	
	case 3: case 2: case 1: case 0:
			//executa essa linha
			break
	
	default:
			//executa esa linha caso nenhuma das condições anteriores sejam válidas
			//ou caso o default nao seja colocado no final
}
//cai aqui após executar a linha do case
```

# Estruturas de Repetição

### WHILE (enquanto condição)

```jsx
//let condicao_verdadeira = true

while (condicao_verdadeira){
		//executa loucamente
}
```

### DO WHILE

```jsx
do {
		//executa uma primeira vez e nas próximas apenas se o valor
		//da condição ainda for válida
} while (condicao_verdadeira)
```

### FOR

```jsx
//equivalente ao FOR apenas com While
let contador = 1
while (contador <= 10) {
		console.log(`contador = ${contador}`)
		contador++
}

//o FOR:
for (let i = 1; i <= 10; i++){
		console.log(`i = ${i}`)
}
```

Pode ser utilizado para percorrer arrays (embora exista outras maneiras melhores que serão vistas no capítulo de arrays)

```jsx
const valores = [6.7, 7.4, 5.5, 9.7, 8.0]

for (let i = 0; i < valores.length; i++){
	console.log(`valor ${i} = ${valores[i]}`)
}
```

### FOR / IN (retorna o índice do elemento de uma lista ou objeto)

```jsx
const valores = [6.7, 7.4, 5.5, 9.7, 8.0]

for (let i in valores){
		console.log(i, valores[i])
}

// 0 6.7
// 1 7.4
// 2 5.5
// 3 9.7
// 4 8

```

```jsx
const pessoa = {
		nome: 'Gustavo',
		sobrenome: 'Prazeres',
		idade: 22,
		altura: 1.8
}

for (let atributo in pessoa){
		console.log(`${atributo} = ${pessoa[atributo]}`)
}
```

### FOR / OF (retorna o conteúdo do elemento)

```jsx
const valores = [6.7, 7.4, 5.5, 9.7, 8.0]

for (let i of valores){
		console.log(i)
}

// 6.7
// 7.4
// 5.5
// 9.7
// 8
```

### BREAK / CONTINUE

```jsx
const valores = [6.7, 7.4, 5.5, 9.7, 8.0]

for (let i in valores){
		if (valores[i] == 5.5){
			break  //interrompe todo o laço
		}
		console.log(`${valores[i]} nao eh 5.5`)
}

// 0 nao eh 5.5
// 1 nao eh 5.5
// --fim do codigo

const valores = [6.7, 7.4, 5.5, 9.7, 8.0]

for (let i in valores){
		if (valores[i] == 5.5){
			continue //interrompe loop atual e pula para próxima repetição
		}
		console.log(`${valores[i]} nao eh 5.5`)
}

// 6.7 nao eh 5.5
// 7.4 nao eh 5.5
// 9.7 nao eh 5.5
// 8 nao eh 5.5
// --fim do codigo
```