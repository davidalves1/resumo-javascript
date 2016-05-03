# Datas

## Referências

- https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date

Uma data é criada através da função construtora new Date(), pegando a data atual

```js
var hoje = new Date();
console.log(hoje);
```

Passando dia e hora específicos com: new Date("dThgmt"), onde:
- d = data, passando no formato yyyy-mm-dd. São aceitos outros formatos, porém esse é certo que funciona
- T = esse caractere é informado para separar a hora da data
- h = hora, pode ser informado só a hora, ou só hora e minutos ou a hora completa, no formato 10:35:42
- gmt = é o fuso em relação a Grenwitch. No caso do Brasil é passado o valor -03:00

```js
var diaEspecifico = new Date("2016-03-08T14:00-03:00");
console.log(diaEspecifico);
```

A função .parse(a), passa o tempo para milissegundos para ser utilizado na função Date().

> Não são todos os formatos de data que são aceitos em JavaScript. O brasileiro, 29/04/2016, não funciona.

```js
var milissegundos = Date.parse("2015-12-24");
console.log(milissegundos);
```

A API do Date é complexa, pois tem várias 'pegadinhas', mas é muito bem explicada no link da referência
