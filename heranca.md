# Herança

### Criando um objeto utilizando funções:

Função Fábrica

```js
var homemFactory = function (nome, idade) {
    return {
        nome: nome,
        idade: idade,
        sexo: "masculino"
    }
}

var jailson = homemFactory("Jailson", 42);
var ze = homemFactory("José", 33);
console.log(jailson);
console.log(ze);
```

Função Construtora

```js
var Homem = function (nome, idade) {
    this.nome = nome;
    this.idade = idade;
}

// O objeto sexo é passado pelo prototype do método Homem, ou seja,
// todos os objetos criados através do método Homem herdarão o valor de sexo,
// pois ele é injetado pelo operador 'new'
Homem.prototype.sexo = "masculino";

var pedro = new Homem("Pedro", 36);
var tiago = new Homem("Tiago", 18);
console.log(pedro);
console.log(tiago);
```

O que o operador new faz é bem semlhante a isso:

```js
var _new = function (f) {
    var res = {};
    if (f.prototype !== null) {
        res.__proto__ = f.prototype;
    }

    var ret = f.apply(res, Array.prototype.slice.call(arguments, 1));
    if ((typeof ret === "object" || typeof res === "function") && ret !== null ) {
        return ret;
    }

    return res;
};

var josue = _new (Homem, "Josué", 42);
console.log(josue, josue.sexo);
```

Toda função tem um prototype, que aponta para um Object.prototype que por sua vez aponta para null
