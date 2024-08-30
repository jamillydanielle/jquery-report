# Tópicos Avançados sobre o JQuery

## Plugins

O jQuery oferece suporte a plug-ins que adicionam novos métodos e funcionalidades. Saiba como criar seu próprio plug-in ou usar os existentes.

## Exemplo simples de criação de um plugin

O plugin mudaCor permite aplicar estilos personalizados a elementos HTML selecionados. Especificamente, ele altera a cor do texto e o tamanho da fonte dos elementos. Aqui está um resumo das suas funcionalidades:

Definição do Plugin: O plugin é definido como uma função que é anexada ao objeto jQuery através do $.fn. Isso permite que ele seja chamado em qualquer seleção de elementos jQuery.

```javascript
(function($) {
  $.fn.mudaCor = function(options) {
    var settings = $.extend({
      cor: 'red',
      tamanho: '14px'
    }, options);

    return this.each(function() {
      $(this).css({
        color: settings.cor,
        fontSize: settings.tamanho
      });
    });
  };
})(jQuery);
```

Opções:

cor: Define a cor do texto dos elementos. O valor padrão é 'red'.
tamanho: Define o tamanho da fonte dos elementos. O valor padrão é '14px'.
O método $.extend é usado para combinar as opções padrão com as opções fornecidas pelo usuário quando o plugin é chamado.

Aplicação do Estilo: O plugin aplica o estilo usando o método .css() do jQuery. Ele altera a cor e o tamanho da fonte dos elementos selecionados com base nas opções fornecidas.

Exemplo de Uso:

```javascript
mudaCor$('#elemento').mudaCor({
  cor: 'blue',
  tamanho: '18px'
});
```

No exemplo acima, o plugin é chamado no elemento com o ID #elemento, alterando a cor do texto para azul e o tamanho da fonte para 18 pixels.


## Exemplos de Utilização de Plugins prontos

### Slider com jQuery vs JavaScript Puro

**jQuery:**

```javascript
$("#slider").slider({
  min: 0,
  max: 100,
  slide: function(event, ui) {
    console.log(ui.value);
  }
});
```
**JavaScript Puro:**

```javascript
const slider = document.getElementById('slider');
slider.addEventListener('input', (event) => {
  console.log(event.target.value);
});
```

### Carrosel com jQuery vs JavaScript Puro

**jQuery:**

```javascript
$('.carousel').carousel({
  interval: 2000,
  wrap: true
});
```

**JavaScript Puro:**

```javascript
let currentIndex = 0;
const items = document.querySelectorAll('.carousel .item');

function showItem(index) {
  items.forEach((item, i) => {
    item.style.display = i === index ? 'block' : 'none';
  });
}
setInterval(() => {
  currentIndex = (currentIndex + 1) % items.length;
  showItem(currentIndex);
}, 2000);
```

### Validação de formulário com jQuery vs JavaScript Puro

**jQuery:**

```javascript
$("#formulario").validate({
  rules: {
    username: "required",
    email: {
      required: true,
      email: true
    }
  },
  messages: {
    username: "Digite seu nome",
    email: "Digite um email válido"
  }
});
```

**JavaScript Puro:**

```javascript
const form = document.getElementById('myForm');

form.addEventListener('submit', (event) => {
  const username = document.getElementById('username');
  const email = document.getElementById('email');

  if (!username.value) {
    alert('Digite seu nome');
    event.preventDefault();
  } else if (!email.value || !/\S+@\S+\.\S+/.test(email.value)) {
    alert('Digite um email válido');
    event.preventDefault();
  }
});
```

## Otimização de performance

As técnicas para otimizar o desempenho do jQuery incluem minimizar as manipulações do DOM e usar a delegação de eventos, veja alguns exemplos:


### Manipulação de DOM em Massa

Para otimizar a manipulação do DOM, especialmente ao adicionar muitos elementos, é recomendável usar document.createDocumentFragment() para evitar múltiplas re-renderizações do DOM.

Exemplo:

```javascript
var fragment = $(document.createDocumentFragment());
for (var i = 0; i < 100; i++) {
  fragment.append('<div>Item ' + i + '</div>');
}
$('#container').append(fragment);
```

### Delegação de Eventos

Ao invés de adicionar ouvintes de eventos diretamente a muitos elementos filhos, use a delegação de eventos com on() para melhorar a performance.

Exemplo:

```javascript
$('#parent').on('click', '.child', function() {
  alert('clicou no child!');
});
```

## Boas práticas no uso do jQuery

Seguir boas práticas de programação com jQuery não apenas melhora a performance e a legibilidade do código, mas também facilita a manutenção e a escalabilidade da sua aplicação. Criar seus próprios scripts e plugins permite que você adicione funcionalidades personalizadas de forma organizada e reutilizável.

Minimizar Manipulações do DOM: Evite fazer alterações frequentes no DOM diretamente; ao invés disso, faça todas as alterações de uma vez.
Delegação de Eventos: Utilize a delegação de eventos para melhorar a performance, especialmente em elementos que são adicionados dinamicamente.
Cache de Seletor: Armazene em cache os seletores jQuery que são usados frequentemente para evitar buscas repetidas.
Uso de Plugins: Utilize plugins validados e bem mantidos para garantir compatibilidade e performance.
