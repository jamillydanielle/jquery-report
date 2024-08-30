# Características do jQuery com exemplos

### As principais características do jQuery são:

- **Manipulação do DOM:** Simplifica o processo de percorrer e manipular o DOM.

```javascript
<script>
  $('#mudar-texto').click(function() {
    $('#content').text('Texto alterado').addClass('novo-estilo');
  });
</script>
```
No exemplo acima:
Estamos alterando o conteúdo de um elemento e adicionamos uma nova classe.
Encontra-se o elemento com o ID content e altera seu texto.
O método ".addClass()" Adiciona uma nova classe "novo-estilo" ao elemento.


- **Tratamento de eventos:** Oferece uma maneira unificada de tratar eventos em diferentes navegadores.

```javascript
<script>
  $('#botao-alerta').click(function() {
    alert('Clicou!');
  });
</script>
```
No exemplo acima:
Estamos capturando o clique em um botão e exibimos um alerta.
O método ".click(function() {...})" Define um manipulador de eventos que será executado quando o botão for clicado. Essa abordagem funciona consistentemente em todos os navegadores.


- **AJAX:** Simplifica a realização de solicitações HTTP assíncronas.

```javascript
<script>
  $('#carregar-dados').click(function() {
    $.ajax({
      url: 'dados.txt',
      success: function(dados) {
        $('#resultado').html(dados);
      }
    });
  });
</script>
```
No exemplo acima:
Estamos carregando conteúdo de um arquivo externo e o inserimos em um elemento da página.
O método "$.ajax({...})" realiza uma solicitação HTTP assíncrona.
Precisamos informar o caminho para o arquivo ou recurso a ser consumido na variável "url".
Função de callnack "success:" é chamada quando a solicitação é bem-sucedida, inserindo os dados no elemento #resultado.


- **Animation:** Oferece métodos para animar propriedades javascript.

```javascript
<script>
  $('#liga-desliga-animacao').click(function() {
    $('#box').slideToggle();
  });
</script>
```

No exemplo acima:
Estamos deslizando um elemento para dentro e para fora da visão
O método ".slideToggle()" anima a altura de um elemento, deslizando-o para dentro e para fora da visão de forma suave.


Para obter uma lista completa dos recursos, consulte: [official documentation](https://api.jquery.com/).
