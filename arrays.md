# Arrays

## Referências
- https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Array

Iniciando um array já setando os valores

```js
var cars = ['Fox', 'Palio', 'Celta'];
console.log(cars);
```

Adiciona um item no fim do array

```js
cars.push('Ka');
console.log(cars);
```

Remove um item do fim do array

```js
cars.pop();
console.log(cars);
```

Adiciona um item no início do array

```js
cars.unshift('Gol');
console.log(cars);
```

Remove um irem do início do array

```js
cars.shift();
console.log(cars);
```

Splice, modifica um array. arr.splice(a, b, c, ... n);
- a = posição de início da modificação
- b = quantidade de itens a serem removidos da posição inicial para frente
- c, ... n = itens a serem inseridos. Podem ser inseridos quantos itens forem necessários

```js
cars.splice(1, 0, 'Cruze', 'Jetta', 'Renegade');
console.log(cars);

cars.splice(2, 2, 'Toro', 'Strada');
console.log(cars);
```

For Each:

```js
cars.forEach(function(value, key) {
    console.log(key + ': ' + value);
});

cars.forEach(function(value) {
    console.log(value);
});
```

## Filtros

Verifica aqueles que atendem:

```js
var fullCars = [
    {nome: 'Gol', marca: 'Volkswagen', preco: 35900},
    {nome: 'Fox', marca: 'Volkswagen', preco: 39000},
    {nome: 'Amarok', marca: 'Volkswagen', preco: 89500},
    {nome: 'Celta', marca: 'GM', preco: 32300},
    {nome: 'Palio', marca: 'Fiat', preco: 35790},
    {nome: 'Toro', marca: 'Fiat', preco: 72000}
];

var fiatCars = fullCars.filter(function(elemento) {
    return elemento.marca === 'Fiat';
});
console.log(fiatCars);
```

Verifica se existe algum:

```js
var someGM = fullCars.some(function(elemento) {
    return elemento.marca === 'GM';
});
console.log('Algum GM? '+ someGM);
```

Verifica se todos são:

```js
var allVolks = fullCars.every(function(elemento) {
    return elemento.marca === 'Volkswagen';
});
console.log('Todos da Volks? ' + allVolks);
```

Gerando novos arrays apartir de outro com map()

```js
var marcas = fullCars.map(function(elem) {
    return elem.marca;
});
console.log(marcas);
```

Somando valores de um array com array.reduce(function(a, b){ ... }, c).
- a = elemento anterior;
- b = elemento atual;
- c = valor inicial;

```js
var totalPreco = fullCars.reduce(function(previous, current) {
    return previous + current.preco;
}, 0);
console.log(totalPreco);
```

Capturando parte de um array com o array.slice(a, b)
- a = índice do valor inicial;
- b = índice - 1 do valor final.

```js
var sliceCars = fullCars.slice(1, 4);
console.log(sliceCars);
```

Invertendo a ordem dos valores do array com array.reverse();
> Lembrando que, diferente das outras funções, ele altera a estrutura do array original

```js
console.log(cars);
console.log(cars.reverse());
// Voltando para a posição original
cars.reverse();
```

Ordenando valores do array com array.sort();
> Somente array.sort() num array com strings ele ordena por ordem alfabetica;

```js
var letras = ['f', 'c', 'd', 'b', 'a', 'e'];
console.log(letras.sort());
```

O sort também pode ordenar por outros tipos de valores.
Crescente:

```js
var carsPriceAsc = fullCars.sort(function(a, b) {
    return a.preco - b.preco;
});
console.log('Preço crescente:');
console.log(carsPriceAsc);
```

Decrescente:

```js
var carsPriceDesc = fullCars.sort(function(a, b) {
    return b.preco - a.preco;
});
console.log('Preço decrescente:');
console.log(carsPriceDesc);
```

Gerando uma string apartir de um array com array.join(a), onde a = separador:

```js
console.log(cars.join(';'));
console.log(cars.join('/'));
console.log(cars.join(' - '));
```

Truque para multiplicar strings:

```js
console.log(new Array(10));
console.log(new Array(10).join('JavaScript'));
```
