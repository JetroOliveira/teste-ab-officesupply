# Como publicar as duas versões (para gerar as URLs da entrega)

Você precisa de duas URLs públicas: uma da versão A e uma da versão B.
Escolha **uma** das opções abaixo. A primeira é a mais rápida.

---

## Opção 1 — Netlify Drop (mais fácil, sem instalar nada)

1. Acesse **https://app.netlify.com/drop**
2. Arraste a pasta **`versao-controle`** para a página
3. Espere alguns segundos — o Netlify gera uma URL tipo
   `https://nome-aleatorio.netlify.app/product-page-control.html`
4. **Copie e guarde essa URL** (é a versão A)
5. Clique em "Sites" → arraste agora a pasta **`versao-variante-b`**
6. Copie essa segunda URL (é a versão B)
7. Se quiser, entre na conta gratuita para renomear os sites para algo como
   `officesupply-controle` e `officesupply-variante-b` — fica mais apresentável na entrega

> Precisa de conta? Não para o Drop. Se pedir login, crie uma conta gratuita com o Google.

---

## Opção 2 — GitHub Pages (se você já tem conta no GitHub)

```bash
# dentro da pasta da entrega
git init
git add .
git commit -m "Teste A/B OfficeSupply"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/teste-ab-officesupply.git
git push -u origin main
```

Depois, no repositório: **Settings → Pages → Branch: main → Save**.
As URLs ficam:

- Controle: `https://SEU-USUARIO.github.io/teste-ab-officesupply/versao-controle/product-page-control.html`
- Variante: `https://SEU-USUARIO.github.io/teste-ab-officesupply/versao-variante-b/produto-variante-b.html`

---

## Opção 3 — Se o professor aceitar local (só se ele pedir para rodar)

Ambas as versões funcionam abrindo o HTML direto no navegador, sem servidor.
Só cite isso se não conseguir publicar.

---

## O que escrever na entrega

Depois de publicar, cole na sua resposta:

```
Versão de Controle (A): <URL 1>
Versão Variante (B):   <URL 2>
Código da variante:    TesteAB-OfficeSupply-Entrega.zip (anexo)
```

---

## Antes de entregar, confira as duas URLs

Abra cada uma no navegador e verifique:

- [ ] A versão **A** mostra o preço **sem** o bloco verde de oferta
- [ ] A versão **B** mostra **"De R$ 379,90"**, o selo **"21% OFF"** e **"Você economiza R$ 80,00"**
- [ ] As **imagens do produto aparecem** nas duas (o zip já inclui `img001.jpeg` e `mouse.jpg` —
      elas precisam estar na mesma pasta do HTML)
- [ ] O botão "Adicionar ao Carrinho" aparece nas duas

Se a imagem não carregar, é porque o HTML e o `img001.jpeg` não estão na mesma pasta no serviço de
hospedagem. Suba a pasta inteira, não só o arquivo HTML.
