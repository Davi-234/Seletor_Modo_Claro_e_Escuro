# Descrição
Um seletor customizado, com temática de dia e noite, para alternar entre os modos escuro (noite) e claro (dia) de um site. O seletor é feito inteiramente com HTML e CSS, utilizando JavaScript apenas para tornar possível o clique no seletor. 

### Tecnologias:
- HTML
- CSS
- JS

## Demonstração do seletor
![Demonstração](demonstracao_seletor)

### CSS
O CSS é composto por pseudo-elementos, classes e animações de transição responsáveis pela mudança das cores do seletor e do botão interno, bem como pelo deslocamento do botão para o início ou para o final do seletor.
O elemento `#btn-seletor` é posicionado sobre o seletor, cuja posição é definida como relativa. Isso permite que o botão se sobreponha ao seletor, criando a sensação de que o componente constitui uma variação de um campo de entrada (`input`) padrão do HTML.

```css
/* ---------------- Estilo padrão do seletor ---------------- */
#seletor {
    background: linear-gradient(90deg,#FFD54F,#4FC3F7,#87CEEB);            
    width: 100px;
    height: 30px;
    border-radius: 30px;
    padding: 3px 3px 5px 5px;
    transition: all .8s ease;
    position: relative;
    overflow: hidden;

    margin-left:0;
}
#seletor::after{
    content:"";
    position:absolute;
    inset:0;
    background:linear-gradient(90deg,#071330,#132A63,#263238);
    opacity:0;
    transition:opacity .8s ease;
    border-radius:30px;
}

    /* seletor para modo escuro */
#seletor.dark_mode::after{
    opacity:1;
}
/* ---------------------------------------------------------- */

/* ----------------- Botão interno do seletor --------------- */
#btn_seletor{
    position:relative;
    z-index:1;
}
#btn_seletor {
    background-color: yellow;
    border-radius: 50%;
    width: 30px;
    height: inherit;    
    transition: all .8s ease;
    margin-left: 0; /* Restaura a margem esquerda ara zero, assim o botão volta para a posição inicial*/
}

    /* Botão do seletor para o modo escuro */
#seletor.dark_mode #btn_seletor {
    background-color: white; /* Muda a cor para o branco, para assemelhar-se a lua */
    margin-left: 67px; /* Adiciona uma margem de 67 pixels (ou seja, a largula do seletor menos o padding direito) */
}
/* ---------------------------------------------------------- */
```

### HTML
```html
<div id="seletor">
        <div id="btn_seletor"></div>
</div>
```

### JS
É adicionado um evento de clique ao seletor, quando o seletor é pressionado, a classe do mesmo é alterado para "dark-mode" quando a classe atual é a "ligth-mode" (estilo padrão do seletor), ou para a padrão quando a classe atual é a "dark-mode".
```js
document.getElementById('seletor').addEventListener('click', function () {
        this.classList.toggle('dark_mode');
});
