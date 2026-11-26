# Teste A/B — OfficeSupply Online
**Jetro Pereira Oliveira · Experiência do Usuário · FATEC Cotia**

---

## 1. Ponto de alavancagem

**Problema:** os produtos de alta margem não vendem porque a página mostra o preço "seco" (R$ 299,90), sem nenhuma referência de valor. O cliente compara com um kit genérico mais barato e não vê motivo para pagar mais.

**Hipótese:** se o preço vier ancorado (valor riscado + desconto + economia + parcelamento), a percepção de valor sobe e a conversão aumenta.

**Onde:** na página do produto, no bloco de preço logo acima do botão "Adicionar ao Carrinho" — é onde a decisão acontece.

---

## 2. Versões de teste

**A (controle):** a página original, preço único.

**B (variante):** muda **só o bloco de preço**. Foto, título, descrição e botão ficam idênticos — assim o resultado pode ser atribuído a uma causa só.

| Elemento | A | B |
|---|---|---|
| Preço original | — | De R$ 379,90 (riscado) |
| Preço atual | R$ 299,90 | R$ 299,90 |
| Desconto | — | 21% OFF |
| Economia | — | R$ 80,00 |
| Parcelamento | — | 6x de R$ 49,98 |

Base: ancoragem de preço (comparar com R$ 379,90, não com zero) + quebra do valor em parcelas pequenas.

---

## 3. Configuração

- **Ferramenta:** VWO (o Google Optimize foi descontinuado em 2023).
- **Divisão:** 50/50. O preço é o elemento mais sensível da página; metade do tráfego chega ao resultado mais rápido e divide o risco.
- **Período:** 2 a 4 semanas. Com add-to-cart de 5% e melhora esperada de 20%, o cálculo pede **~8.160 visitas por versão**. Abaixo de 2 semanas a amostra não fecha; acima de 4 o teste envelhece e sofre com promoções e sazonalidade.

---

## 4. Métricas

**Primária:** taxa de adição ao carrinho — é o que a mudança afeta diretamente.

**Secundárias:** conversão final, receita por visitante, ticket médio, rejeição/tempo na página e **margem de contribuição por pedido** (vender mais com desconto pode lucrar menos).

**Monitoramento:** VWO (experimento e significância), GA4 (view_item, add_to_cart, purchase) e Microsoft Clarity (mapa de calor — o cliente lê o bloco novo ou passa direto?).

---

## 5. Análise e decisão

1. Rodar o período completo **sem espiar** o resultado no meio (parar quando está ganhando gera falso positivo).
2. Confirmar a amostra mínima; se não bateu, estender até 4 semanas.
3. Comparar as taxas e exigir **p < 0,05**, olhando também o intervalo de confiança (tamanho do ganho, não só a existência).
4. Cruzar com margem por pedido e segmentar por dispositivo e origem de tráfego.

**Decisão:**
- **B vence com significância e margem estável** → publicar para 100% e replicar nos outros produtos de alta margem.
- **Empate** → manter A. Preço não era o gargalo; o próximo teste ataca prova social, descrição ou frete.
- **B perde** → reverter. Vender menos com desconto é o pior cenário.

---

## Entregas

**Código:** `versao-controle/` (A) e `versao-variante-b/` (B), no zip e no repositório.

- Controle (A): https://jetrooliveira.github.io/teste-ab-officesupply/versao-controle/product-page-control.html
- Variante (B): https://jetrooliveira.github.io/teste-ab-officesupply/versao-variante-b/produto-variante-b.html
- Índice: https://jetrooliveira.github.io/teste-ab-officesupply/
- Repositório: https://github.com/JetroOliveira/teste-ab-officesupply
