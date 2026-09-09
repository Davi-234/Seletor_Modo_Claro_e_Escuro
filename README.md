# Descrição
Um seletor customizado, com temática de dia e noite, para alternar entre os modos escuro (noite) e claro (dia) de um site.
### Tecnologias:
O seletor é feito inteiramente com HTML e CSS, utilizando Javascript apenas para tornar possível o clique no seletor. O CSS é composto por pseudo-seletores e animações de transcição para a mudança das cores do seletor e do botão dentro dele.

## Demonstração Seletor
![Semonstração](demonstracao_seletor)

### CSS

```css
#seletor {
    background: linear-gradient(90deg, #FFD54F, #4FC3F7, #87CEEB);
    width: 100px;
    height: 30px;
    border-radius: 30px;
    padding: 3px 3px 5px 5px;
    transition: all 0.8s ease;
    position: relative;
    overflow: hidden;
    margin-left: 0;
}

#seletor::after {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(90deg, #071330, #132A63, #263238);
    opacity: 0;
    transition: opacity 0.8s ease;
    border-radius: 30px;
}

#seletor.dark_mode::after {
    opacity: 1;
}

#btn_seletor {
    position: relative;
    z-index: 1;
    background-color: yellow;
    border-radius: 50%;
    width: 30px;
    height: inherit;
    transition: all 0.8s ease;
    margin-left: 0;
}

#seletor.dark_mode #btn_seletor {
    background-color: white;
    margin-left: 67px;
}
```

### HTML
```html
<div id="seletor">
        <div id="btn_seletor"></div>
</div>
```

### JS
```js
document.getElementById('seletor').addEventListener('click', function () {
        this.classList.toggle('dark_mode');
});
```
