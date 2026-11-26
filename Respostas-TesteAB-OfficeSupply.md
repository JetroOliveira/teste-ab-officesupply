# Prova de UX — Teste A/B OfficeSupply Online
### Respostas para copiar

---

## 1. Identificação do Ponto de Alavancagem

**Problema / hipótese:**

Os produtos de alta margem não vendem porque a página mostra o preço seco, sem nenhuma
justificativa de valor. O cliente vê "R$ 299,90" e compara com um kit genérico mais barato — ele
não tem como saber que está levando algo melhor, nem que está fazendo um bom negócio.

Minha hipótese: **se a página mostrar que aquele preço é uma oferta (valor original riscado,
percentual de desconto, quanto ele economiza e o parcelamento), o cliente percebe valor e a
conversão sobe nesses produtos.**

**Local de aplicação:**

Página de detalhes do produto (PDP), no bloco de preço — a área imediatamente acima do botão
"Adicionar ao Carrinho". Escolhi esse ponto porque é onde o cliente decide: ele já viu a foto e o
nome, e está olhando o preço para decidir se continua.

---

## 2. Desenvolvimento das Versões de Teste

**Versão de Controle (A):** a página original do anexo. O preço aparece como um número só:

> R$ 299,90

**Versão Variante (B):**

Uma alteração, só no bloco de preço. O resto da página fica idêntico — mesma foto, mesmo título,
mesma descrição, mesmo botão. Isso é importante: se eu mexer em várias coisas ao mesmo tempo, depois
não dá para saber o que causou o resultado.

O que muda:

| Elemento | Controle (A) | Variante (B) |
|---|---|---|
| Preço original | não aparece | "De R$ 379,90" riscado |
| Preço atual | R$ 299,90 | R$ 299,90 |
| Desconto | não aparece | selo "21% OFF" |
| Economia | não aparece | "Você economiza R$ 80,00" |
| Parcelamento | não aparece | "ou 6x de R$ 49,98 sem juros" |

A lógica é ancoragem de preço: em vez de o cliente comparar R$ 299,90 com zero, ele compara com
R$ 379,90. E o "6x de R$ 49,98" quebra o valor grande em parcelas pequenas.

Tudo em um bloco com fundo verde claro e borda, para separar do resto do texto sem parecer anúncio
agressivo.

---

## 3. Configuração e Aplicação do Teste A/B

**Ferramenta:** VWO (Visual Website Optimizer). O Google Optimize foi descontinuado em setembro de
2023, então citei o VWO como ferramenta real — e ele faz exatamente o que o exercício pede: editor
visual, divisão de tráfego, cálculo de significância e relatório de resultado.

**Divisão de tráfego:** 50/50. Metade dos visitantes vê a A, metade vê a B. Optei por metade e não
70/30 porque o preço é o elemento mais sensível da página — se a variante prejudicar a venda, o
prejuízo é direto. 50/50 chega ao resultado no menor tempo possível e distribui o risco por igual.

**Período do teste:** mínimo de 2 semanas, máximo de 4.

Justificativa: com uma taxa de adição ao carrinho em torno de 5% e uma melhoria esperada de 20%
(para 6%), o cálculo de amostra pede cerca de **8 mil visitas por versão**. Em 2 semanas a maioria
das lojas de médio porte atinge isso; abaixo disso o resultado não é confiável. Quatro semanas é o
teto para capturar dois ciclos completos de compra (inclusive a diferença entre semana e fim de
semana) sem deixar o teste velho — depois disso, promoções e sazonalidade começam a contaminar.

---

## 4. Definição e Monitoramento de Parâmetros e Métricas

**Métrica primária (KPI):** taxa de adição ao carrinho (add-to-cart rate) do produto em teste —
quantos visitantes da página clicaram em "Adicionar ao Carrinho", dividido pelo total de visitantes.

Escolhi essa e não "receita" porque é a métrica que a alteração consegue mover diretamente. Receita
depende de frete, cupom e desistência no checkout, coisas que o teste não toca.

**Métricas secundárias:**

- **Taxa de conversão final** (compra concluída) — confirma se o clique virou venda de verdade
- **Receita por visitante** — mede se o desconto trouxe volume sem derrubar o faturamento
- **Ticket médio** — verifica se o cliente passou a levar o kit sozinho ou junto com outros itens
- **Taxa de rejeição e tempo na página** — garante que o bloco novo não afastou nem confundiu
- **Margem de contribuição por pedido** — o ponto do exercício: vender mais com desconto pode dar
  menos lucro. Se a receita subir e a margem cair, a variante não serve.

**Ferramentas de monitoramento:**

- **VWO** — roda o experimento, divide o tráfego e calcula a significância
- **Google Analytics 4** — eventos `view_item`, `add_to_cart` e `purchase`, para cruzar o resultado
  com o funil inteiro
- **Microsoft Clarity** — mapa de calor e gravação de sessão, para ver se o cliente lê o bloco novo
  ou passa direto (gratuito e sem limite de sessões)

---

## 5. Avaliação de Desempenho e Indicação do Melhor Resultado

**Processo de análise:**

1. Espero o período fechar sem espiar o resultado no meio — olhar todo dia e parar quando está
   ganhando infla o erro e produz falso positivo.
2. Confiro se a amostra planejada foi atingida (≥8 mil por versão). Se não, estendo até o limite de
   4 semanas.
3. Comparo a taxa de adição ao carrinho das duas versões no VWO e observo o **p-valor**. Adoto
   p < 0,05 com 95% de confiança: abaixo disso, a diferença é real e não sorte.
4. Verifico o **intervalo de confiança** da diferença — quero saber o tamanho do ganho, não só que
   ele existe.
5. Cruzo com as secundárias: rejeição, tempo na página e, principalmente, **margem por pedido**. Se
   a conversão subiu mas a margem caiu, o teste falhou no objetivo do negócio, mesmo com número
   bonito.
6. Segmento por dispositivo e por origem de tráfego, para não perder um efeito escondido (mobile
   pode reagir diferente do desktop).

**Recomendação:**

- **Se a B ganhar com significância e a margem se mantiver:** publico a variante para 100% do
  tráfego e aplico o mesmo bloco de oferta nos outros produtos de alta margem, começando pelos de
  maior contribuição. Depois abro um novo teste em cima do vencedor.
- **Se não houver diferença significativa:** mantenho a A. Um resultado empatado já é informação —
  significa que preço não era o gargalo, e o próximo teste deve atacar outro ponto (prova social,
  descrição ou frete).
- **Se a B perder:** reverto imediatamente e registro o aprendizado. Perder com desconto é o pior
  cenário: vendo menos e com margem menor.

---

## Entregas

**Código da versão variante:** `produto-variante-b.html` + `style-variante-b.css` (no zip).
Construída a partir do HTML original, com apenas o bloco de preço alterado.

**URLs publicadas (GitHub Pages):**

- Versão de Controle (A): https://jetrooliveira.github.io/teste-ab-officesupply/versao-controle/product-page-control.html
- Versão Variante (B): https://jetrooliveira.github.io/teste-ab-officesupply/versao-variante-b/produto-variante-b.html
- Índice com as duas versões: https://jetrooliveira.github.io/teste-ab-officesupply/

Repositório com o código: https://github.com/JetroOliveira/teste-ab-officesupply
