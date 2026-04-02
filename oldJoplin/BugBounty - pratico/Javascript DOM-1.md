Javascript DOM

Each DOM node object has a nodeType property, which contains a code (number) that identifies the type of node. Elements have code 1, which is also defined as the constant property Node.ELEMENT\_NODE. Text nodes, representing a section of text in the document, get code 3 (Node.TEXT\_NODE). Comments have code 8 (Node.COMMENT_NODE).

pensa numa arvore, as folhas sao os textos, e as flexas indicam a relacao parent-child

**![2b00d50d146789c6940b855d23b27b97.png](../_resources/2b00d50d146789c6940b855d23b27b97-1.png)**

**![98a5a6508fc4070f52dc26078a37320e.png](../_resources/98a5a6508fc4070f52dc26078a37320e-1.png)**

**curso em video a arvore comeca com a root no navegador e a root eh o window**

**dentro de window tem location, document, history e muitos outros**

**<img src="../_resources/f4ceeb81323eeab809a63e49d1997931-1.png" alt="f4ceeb81323eeab809a63e49d1997931.png" width="321" height="189">**

**<img src="../_resources/aac7ca1de7cb7bf1d83a31d85a596621-1.png" alt="aac7ca1de7cb7bf1d83a31d85a596621.png" width="371" height="646">**

**da pra selecionar por **

**<img src="../_resources/5f129f1cce88a0599f22b1db80f19def-1.png" alt="5f129f1cce88a0599f22b1db80f19def.png" width="226" height="309">**

**getElementsByTagName () por marca -> da pra selecionar mais de um objeto**

**getElementById() -> pega somente um**

**getElementsByName() -> pega varios**

**getElementsByClassName() -> classes seletor**

**querySelector('div#msg' )**

**querySelectorAll()**

**.o innerHtml or inner.Text**

**<img src="../_resources/85871128d47c9f658247e08c1e48c3c5-1.png" alt="85871128d47c9f658247e08c1e48c3c5.png" width="422" height="333">**

**var post =  $('section.blog-list h2:contais(Procrastination)')**

**post.get(0) -> DOM element**

**var post =  $('section.blog-list h2:contais(Procrastinatio)')**

**post -> apesar de n ter match ele tem o objeto**

**if (post) {console.log('true');} -> ele existe carai**

**post.get(0).scrollIntoView**

**var post =  $('section.blog-list h2:contais(&lt;h1&gt;test&lt;/h1&gt;)') -> da match lollllll**

**var post = post.get(0) -> eh um dom element mas ele ta detached**

** var mynode = document.getElementById('academyLabHeader') **

**mynode.appendChild(post)**

let myimg = document.createElement('img')

myimg.src = 0 -> o http request eh feito para pegar a imagem. Eh aqui que vc vai se aproveitar

var post =  $('section.blog-list h2:contais(&lt;img src="0" onerror="alert()"&gt;)')

&lt;iframe src=" /#" onload="this.src+='<img src=0 onerror=print()&gt;'">&lt;/iframe&gt;