# Expressões Regulares

## Referências:
- https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Regular_Expressions
- https://www.youtube.com/watch?v=9r48XuOB4DA&index=10&list=PLQCmSnNFVYnT1-oeDOSBnt164802rkegc

### Definindo uma RegExp: ```/<expressão>/```

Existem duas formas de testar a expressão regular: exec() e test()
- exec(): retorna mais dados. Mais completo;
- test(): retorna apenas true, se atendeu a expressão, e false, se não atendeu. Mais prático;

-- Exemplo 1:
```js
var regExp1 = /9999-9999/;
var telefone1 = '9999-9999';
console.log(regExp1.test(telefone1));
```

Em caracteres especiais é necessário usar o caracter de escape '/'

-- Exemplo2:
```js
var regExp2 = /\(48\) 9999-9999/
var telefone2 = '(48) 9999-9999';
console.log(regExp2.test(telefone2));
```
> Obs: a string "O telefone é (48) 9999-9999, ligue agora!", também retorna true, pois a expressão não leva em consideração o que vem antes ou depois da expressão, apenas se ela existe na string.

Os caracteres '^' e '$' indicam que a string deve ter exatamente e expresão entre estes caracteres

-- Exemplo3:
```js
var regExp3 = /^\(48\) 9999-9999$/
var telefone3 = '(48) 9999-9999';
console.log(regExp3.test(telefone3));
```
> Obs: a string "O telefone é (48) 9999-9999, ligue agora!", dessa vez retorna false

Deixando a expressão dinâmica, pois anteriormente só retornava true se os caracteres fossem os mesmos da expressão

-- Exemplo 4:
```js
var regExp4 = /^\([0-9][0-9]\) [0-9][0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]$/
var telefone4 = '(93) 0480-0342';
console.log(regExp4.test(telefone4));
```

Definindo a quantidade de caracteres na expressão
- {n} = define um número exato de caracteres;
- {n,} = define um número mínimo de caracteres;
- {n,m} = define um intervalo de quantidade de caracteres

-- Exemplo 5 :
```js
var regExp5 = /^\([0-9]{2}\) [0-9]{4}-[0-9]{4}$/
var telefone5 = '(64) 6345-8562';
console.log(regExp5.test(telefone5));
```

-- Exemplo 6:
```js
var regExp6 = /^\([0-9]{2}\) [0-9]{4,5}-[0-9]{4}$/
var telefone61 = '(64) 36346-8662';
var telefone62 = '(64) 6346-8662';
console.log(regExp6.test(telefone61), regExp6.test(telefone62));
```

Deixando um caracter ou grupo opcional na expressão com '?'

-- Exemplo 7
```js
var regExp7 = /^\([0-9]{2}\) [0-9]{4,5}-?[0-9]{4}$/
var telefone71 = '(64) 36346-8662';
var telefone72 = '(64) 63468662';
console.log(regExp7.test(telefone71), regExp7.test(telefone72));
```

Aplicando expressões regulares em repetições, como uma tabela, por exemplo.

-- Exemplo8
```js
var regExp8 = /<table><tr>(<td>\([0-9]{2}\) [0-9]{4,5}-?[0-9]{4}<\/td>)+<\/tr><\/table>/
var telefone8 = '<table><tr><td>(64) 36346-8662</td><td>(98) 9939-9289</td><td>(12) 930090262</td></tr></table>';
console.log(regExp8.test(telefone8));
```

Utilizando metacaracteres para representar os grupos
- . = representa qualquer caracter
- \w = [a-zA-Z0-9] (alfanuméricos e números)
- \W = negação do \w
- \d = [0-9]
- \D = negação do \d
- \s = espaço
- \S = não espaço
- \n = quebra de linha
- \t = tab

-- Exemplo 9
```js
var regExp9 = /^\(\d{2}\)\s?\d{4,5}-?\d{4}$/
var telefone91 = '(64)36346-8662';
var telefone92 = '(64) 63468662';
console.log(regExp9.test(telefone91), regExp9.test(telefone92));
```

Extrair os dados de uma string através da expressão regular  
>Neste caso utiliza-se também a API da sting, principalmente match(), split(), replace()

-- Exemplo 10:
```js
var regExp10 = /\(\d{2}\)\s?\d{4,5}-?\d{4}/
var telefone10 = '<table><tr><td>(64) 36346-8662</td><td>(98) 9939-9289</td><td>(12) 930090262</td></tr></table>';
console.log(regExp10.exec(telefone10));
```

É possível observar no exemplo anterior que foi retornado apenas o primeiro valor encontrado.  
Por isso é importante considerar que existem os modificadores de expressões regulares:
- i = case-insensitive matching, não leva em consideração maiúsculas ou minúsculas;
- g = global matching, continua a busca mesmo após ter encontrado a expressão uma vez;
- m = multiline matching, em casos onde haja quebra de linha

-- Exemplo 10:
```js
var regExp11 = /\(\d{2}\)\s?\d{4,5}-?\d{4}/g
var telefone11 = '<table><tr><td>(64) 36346-8662</td><td>(98) 9939-9289</td><td>(12) 930090262</td></tr></table>';
console.log(telefone11.match(regExp11));
```
