javascripto

document.documentElement -> eh o root

document.body

node.nodeType -> inter que identifica o tipo do node. Elementos tem codigo 1

TEXT\_NODE= 3, COMMENT\_NODE=8

Node.ELEMENT_NODE (code 1)

node.childNodes é uma propriedade em array que contem elementos nodes do DOM

é uma instancia do tipo  NodeList mas não um array de verdade por isso n tem metodos slice e map.

document.body.parentNode -> mostra os pais do elemento

existe o firt e last child. previousSibling, e nextSibling

function talksAbout(node, string) {
if (node.nodeType == Node.ELEMENT_NODE) {
for (let child of node.childNodes) {
if (talksAbout(child, string)) {
return true;
}
}
return false;
} else if (node.nodeType == Node.TEXT_NODE) {
return node.nodeValue.indexOf(string) > -1;
}
}
console.log(talksAbout(document.body, "book"));
// → true

remove -> remove um node

appendChild -> adiciona um child node num elemento

insertBefore(elemento a ser add, posicao do elemento) -> muda a posicao do elemento

replaceChild(||, ||) -> substitui os nodes

ao invez de ter uma live node, da pra converter tudo pra uma array real usando Array.from:

let arrayish = {0: "one", 1: "two", length: 2};
let array = Array.from(arrayish);
console.log(array.map(s => s.toUpperCase()));
// → \["ONE", "TWO"\]

o document.querySelectorAll("p") -> pega todos os nodes do DOM, não eh live, mas ainda não é uma array. Tem que usar o Array.from