---
slug: how-bolloprint-works
title: "Design, Peça, Variante, Produto: o mapa do BolloPrint em cinco minutos"
description: As quatro coisas que estão por trás de cada encomenda, a que pergunta responde cada uma e porque são quatro e não uma só ficha. Com um suporte de telemóvel como exemplo, do princípio ao fim.
date: 2026-10-09
updated: 2026-10-12
tags: [tutoriais]
cover: 01-el-mapa.webp
draft: true
---

Chega uma encomenda: **dois suportes de telemóvel, em branco**.

E antes de mexeres um dedo, o BolloPrint já sabe três coisas: **quanto te custa**
fabricá-los, **quanto te deixa** vendê-los e **onde estão os ficheiros** para os
imprimir.

Como é que sabe? Porque por trás dessa linha da encomenda há quatro coisas que
preparaste uma única vez: um **Design**, uma **Peça**, uma **Variante** e um
**Produto**. São as quatro palavras que mais vais ver no BolloPrint. Aqui
contamos-te o que é cada uma, porque são quatro e não uma, e como acabam numa
encomenda.

::animation{id="how-it-works"}

## Quatro perguntas, quatro coisas

A forma mais fácil de não as confundires é pensar na pergunta a que cada uma
responde:

| | Responde a… | O que guarda |
|---|---|---|
| **Design** | O que é? | Os ficheiros 3D (STL, 3MF…), as fotos e as tuas notas. Nem custo nem preço. |
| **Peça** | Como o fabrico? | O material, a cor, o acabamento, o peso e o tempo. **Tem custo.** |
| **Variante** | Por quanto o vendo? | O preço e a margem. **É o que entra numa encomenda.** |
| **Produto** | Como o mostro? | O nome, as fotos e a descrição. Agrupa as variantes. |

Se ficares só com esta tabela, já tens metade do artigo.

## Vamos montá-lo: um suporte de telemóvel

Vamos preparar o suporte da encomenda, pela mesma ordem em que o farias tu.

**1. O Design.** Carregas o STL do suporte e um par de fotos. Isso é o Design: o
modelo e mais nada. Ainda não decidiste em que o vais imprimir, por isso não tem
custo.

**2. As Peças.** Agora decides como o fabricas. Queres em **PLA preto** e em
**PETG branco**: são duas Peças do mesmo Design. Cada uma tem o seu material, o
seu peso e o seu tempo de impressão, por isso cada uma tem **o seu custo**, e o
BolloPrint calcula-o sozinho.

![O detalhe do design do suporte, com as suas duas peças por baixo: PLA preto e PETG branco](/blog/media/2026-10-09-como-funciona-bolloprint/02-diseno-y-piezas.png)

:::info 💡 Uma Peça pertence sempre a um Design
Por isso não há uma lista de Peças à parte: encontras as Peças dentro do Design a
que pertencem.
:::

**3. As Variantes.** Agora decides por quanto o vendes. Crias a Variante «PLA
preto» a **12,90 €** e a Variante «PETG branco» a **15,90 €**. Cada uma sabe de
que Peça é feita, por isso sabe quanto custa, e com o preço calcula sozinha **a
margem**.

**4. O Produto.** Por fim, o que o cliente vê: o Produto «Suporte de telemóvel
ajustável», com o seu nome, as suas fotos e a sua descrição. Lá dentro vão as duas
Variantes, como as opções de cor de qualquer loja online. É o que publicas, por
exemplo, no Etsy.

![As variantes do suporte em separadores, com a de PETG branco aberta: o custo, a margem, o preço e a peça de que é feita](/blog/media/2026-10-09-como-funciona-bolloprint/03-producto-y-variantes.png)

## Porquê quatro e não uma só ficha?

É a pergunta que toda a gente faz, e a resposta é simples: **cada uma das quatro
coisas muda por um motivo diferente.**

- O **Design** muda quando corriges o modelo.
- A **Peça**, quando mudas de material ou te sobe o custo por hora.
- A **Variante**, quando mexes no preço.
- O **Produto**, quando mudas as fotos ou a descrição.

Se tudo vivesse numa só ficha, corrigir o STL obrigava-te a mexer nele em cada
cor que vendes. Separado, corriges uma vez, no Design, e vale para tudo o que
depende dele.

Se te ajudar pensar assim: o Design é a receita, a Peça é o prato cozinhado e a
Variante é o que aparece na ementa, com o seu preço.

### A prova: um pack

Imagina que também vendes um **organizador de cabos**, e te lembras de um pack: o
suporte preto e o organizador juntos, por 19,90 €.

Não é preciso preparar nada de novo. Crias uma Variante «Pack mesa» com **duas
Peças lá dentro**: a do suporte preto e a do organizador. O BolloPrint soma o que
custam as duas e, com o preço, dá-te a margem do pack.

![A variante Pack mesa, feita de duas peças; e a peça do suporte preto, usada ao mesmo tempo pela variante avulsa e pelo pack](/blog/media/2026-10-09-como-funciona-bolloprint/04-variante-de-dos-piezas.webp)

Repara no que acabou de acontecer: **a Peça do suporte preto é agora usada por
duas Variantes**, a avulsa e o pack. Se amanhã o PLA subir, mudas essa Peça uma
só vez, e o BolloPrint avisa-te de que Variantes a usam para reveres o preço
delas. É exatamente essa a razão de Peça e Variante serem coisas diferentes.

E serve igualmente para vender várias iguais: um «Pack x3» é uma Variante com
três vezes a mesma Peça.

![O bloco Peças que compõem a variante, com as duas peças do pack](/blog/media/2026-10-09-como-funciona-bolloprint/05-piezas-de-la-variante.png)

## A encomenda fecha o círculo

Voltemos à encomenda do início.

Quando crias uma encomenda, o que acrescentas **é uma Variante**: procuras
«suporte», escolhes «PETG branco», pões 2 unidades, e o preço preenche-se sozinho.

E como essa Variante sabe de que Peças é feita, a linha da encomenda já traz tudo
o resto:

- **quanto custa e quanto deixa**, porque as Peças têm custo e a Variante tem
  preço;
- **o material, a cor e o peso**, que vêm das suas Peças;
- e **os ficheiros para imprimir**: a partir da linha, a opção **Designs** leva-te
  aos modelos 3D de cada Peça.

Quando já a tiveres impressa, marcas a linha com **Marcar como impresso**, e a
encomenda segue o seu caminho pela Produção.

![Uma encomenda com duas linhas, o suporte branco e o pack, e por baixo as peças que é preciso imprimir para a servir](/blog/media/2026-10-09-como-funciona-bolloprint/06-del-pedido-a-la-impresora.webp)

É isto que as quatro coisas te poupam: não apontas o custo de cada encomenda, não
procuras o STL numa pasta e não recalculas a margem à mão. Preparaste-o uma vez, e
cada encomenda herda-o.

![As linhas de uma encomenda, com o menu aberto na opção Designs](/blog/media/2026-10-09-como-funciona-bolloprint/07-lineas-del-pedido.png)

## Tudo isto de cada vez? Não

Se te parece muito trabalho para um só suporte, calma: para isso existe a
**Criação Rápida**. Dás-lhe o STL, o material, a cor e o preço num só formulário,
e o BolloPrint cria de uma vez o Design, a Peça, a Variante e o Produto.

O melhor é que o resultado é exatamente o mesmo que se o tivesses feito passo a
passo. Por isso, no dia em que quiseres acrescentar outra cor ou montar um pack,
já está tudo no sítio.

![O formulário de Criação Rápida, com o ficheiro, o material, a cor e o preço](/blog/media/2026-10-09-como-funciona-bolloprint/08-creacion-express.png)

:::info 💡 Dúvidas?
Escreve-nos a partir da [página de contacto](/contact) ou abre um tópico no
[nosso Discord](/help/soporte-por-discord). Se nos contares o que vendes,
ajudamos-te a montá-lo.
:::

## Documentação relacionada

- [Catálogo](/help/catalogo) — os quatro níveis, na referência
- [Designs](/help/disenos) — os ficheiros, as fotos e as etiquetas
- [Peças](/help/piezas) — o material e como se calcula o custo
- [Produtos e Variantes](/help/productos-y-variantes) — o preço, a margem e as peças de cada variante
- [Encomendas](/help/pedidos) — da venda à entrega
- [Criação Rápida](/help/creacion-express) — as quatro de uma vez
- [Quanto custa realmente uma peça impressa](/blog/calculate-your-3d-printing-costs) — de onde vem o custo de cada Peça
