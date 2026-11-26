# Teste A/B — OfficeSupply Online

As duas versões já estão publicadas:

| Versão | URL |
|---|---|
| Controle (A) | https://jetrooliveira.github.io/teste-ab-officesupply/versao-controle/product-page-control.html |
| Variante (B) | https://jetrooliveira.github.io/teste-ab-officesupply/versao-variante-b/produto-variante-b.html |
| Índice | https://jetrooliveira.github.io/teste-ab-officesupply/ |

## Arquivos

- `versao-controle/` — página A: `product-page-control.html`, `style-control.css`, imagens.
- `versao-variante-b/` — página B: `produto-variante-b.html`, `style-variante-b.css`, imagens.
- `01-versao-controle-A.png` e `02-versao-variante-B.png` — prints das duas páginas.
- `index.html` — página de índice com links para as duas versões.
- `Respostas-TesteAB-OfficeSupply.md` — as respostas da atividade.

## Diferença entre as versões

Só o bloco de preço. A em `versao-controle/product-page-control.html`:

```html
<div class="product-price">
    <span class="current-price">R$ 299,90</span>
</div>
```

B em `versao-variante-b/produto-variante-b.html`:

```html
<div class="bloco-oferta">
    <span class="preco-de">De R$ 379,90</span>
    <div class="linha-preco">
        <span class="current-price">R$ 299,90</span>
        <span class="badge-off">21% OFF</span>
    </div>
    <p class="economia">Você economiza R$ 80,00</p>
    <p class="parcelas">ou 6x de R$ 49,98 sem juros</p>
</div>
```

## Para usar com o VWO

No editor visual, crie o teste na URL do produto, adicione uma variação e cole o bloco `bloco-oferta` no lugar de `.product-price`. O CSS do bloco está no final de `style-variante-b.css`.
