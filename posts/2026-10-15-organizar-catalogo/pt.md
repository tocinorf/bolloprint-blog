---
slug: organize-your-3d-printing-catalog
title: "De ficheiros STL a produtos na tua loja: como organizar o teu catálogo de impressão 3D"
description: Aprende a estruturar os teus ficheiros STL, a calcular custos por peça e a criar variantes de produtos para a tua loja de impressão 3D sem complicações.
date: 2026-10-18
tags: [tutoriais]
cover: 01-portada.webp
---

Se imprimes em 3D para vender, de certeza que conheces esta cena: dezenas de pastas
no computador com ficheiros chamados `llavero_V2_FINAL_definitivo.stl`, sem te
lembrares de quanto filamento gastava essa versão nem de que perfil de fatiamento
usaste. E quando entra uma encomenda no Etsy, calculas os teus custos a olho e
esperas não perder dinheiro.

Numa oficina ou numa farm de impressão 3D, a confusão técnica e a comercial
cruzam-se se não as separares. Por isso, o BolloPrint trata-as em separado. Neste
guia explicamos-te como encaixam **Designs, Peças, Produtos e Variantes**, para
passares de um monte de ficheiros soltos a um catálogo organizado.

::animation{id="how-it-works"}

## Separa o técnico do comercial

Um dos erros mais habituais ao gerir uma oficina é tratar um ficheiro STL como se
fosse o produto que vendes. Na prática, um mesmo modelo 3D pode ser impresso em
materiais diferentes, ter várias partes ou ser vendido em packs.

Por isso, o BolloPrint organiza o teu catálogo em três níveis.

### Designs: a biblioteca técnica

O **Design** é o contentor dos teus ficheiros de origem: os STL, OBJ ou projetos
3MF, juntamente com as fotos do modelo e as tuas notas internas.

- **Pensa no Design como a planta ou a ideia.** Não leva tempos nem gramas de
  filamento, porque um mesmo STL pode ser impresso a escalas diferentes ou com
  materiais diferentes.

![O design «Keyring BolloPrint», com o seu ficheiro STL, a sua foto, as suas notas internas e as suas duas peças: de 5 cm e de 10 cm](/blog/media/2026-10-15-organizar-catalogo/02-diseno.png)

### Peças: o objeto físico

Uma **Peça** é o resultado de pegar num Design e dar-lhe uma configuração de
impressão concreta: o material e o seu consumo (por exemplo, PLA preto), as
medidas e o tempo de impressão.

- **Um Design, várias Peças.** Com o mesmo STL podes imprimir uma figura em dois
  tamanhos, 5 cm e 10 cm: esse Design terá duas Peças, «Porta-chaves pequeno» e
  «Porta-chaves grande». O mesmo vale para cores ou materiais diferentes.
- **O teu ficheiro fatiado faz as contas.** Se carregares na Peça o ficheiro do
  fatiador (`.gcode`, `.gcode.3mf`, `.bgcode` ou `.goo` de resina), o BolloPrint
  lê o peso e o tempo de impressão e propõe-tos. Ao aplicá-los, calcula quanto te
  custa fabricar exatamente essa peça. Também podes escrever ou corrigir os dados
  à mão.

:::info 💡 Um 3MF de projeto não serve aqui
O fatiador tem de ter fatiado a placa para saber o peso e o tempo. Um `.3mf` de
projeto não os inclui: esse vai no Design. Na Peça, carrega o `.gcode.3mf` que o
fatiador exporta.
:::

### Produtos e Variantes: o que o teu cliente vê e compra

O **Produto** é a tua montra: o que publicas na tua loja ou num marketplace como o
Etsy. A **Variante** é a opção concreta que o cliente escolhe.

- **Uma Variante pode ter uma ou várias Peças**, cada uma com a sua quantidade.
- **Por exemplo:** o teu Produto é «Figura do Bollo», o nosso cão. Uma Variante
  pode ser «Verde», outra «Laranja» e outra o pack «Verde + Laranja», com as duas
  Peças lá dentro. Podes combinar materiais, tamanhos, acabamentos ou lotes como
  quiseres.

![A variante Green+Orange, com as suas duas peças lá dentro, uma laranja e outra verde, e o seu custo, a sua margem e o seu preço](/blog/media/2026-10-15-organizar-catalogo/04-variante-pack.png)

- **A margem calcula-se sozinha.** Como cada Variante sabe de que Peças é feita,
  o BolloPrint compara o teu preço de venda com o custo real de produção e
  mostra-te a margem. Se mudares o preço, a margem atualiza-se, e vice-versa.

![A variante Green, com uma só peça: custo de 7,06 €, margem de 70 % e preço de 23,54 €](/blog/media/2026-10-15-organizar-catalogo/03-variante.png)

## Estás com pressa? Usa a Criação rápida

Se estás a começar ou tens centenas de modelos para carregar, configurar Designs,
Peças e Produtos um a um leva o seu tempo.

Para isso existe o botão **Criação rápida** do catálogo.
Num só ecrã carregas o teu ficheiro 3D, indicas o material, o peso, o tempo e o
preço, e o BolloPrint cria de uma vez o Design, a Peça, o Produto e a sua
Variante. O resultado é o mesmo que se o fizesses passo a passo, por isso depois
podes afinar o que quiseres.

![O formulário da Criação rápida: o ficheiro 3D, as fotos, o material, o peso, o tempo, as cores, o custo e o preço](/blog/media/2026-10-15-organizar-catalogo/05-creacion-express.webp "50%")

## As tuas etiquetas passam sozinhas para o produto

Outro pormenor que te poupa trabalho: as **etiquetas** de um Design passam
sozinhas para os seus Produtos.

Se etiquetares um Design como «Porta-chaves» ou «Figuras», quando adicionares as
suas Peças a uma Variante, essas etiquetas somam-se ao Produto. E se vendes no
Etsy, ao publicar o anúncio já te aparecem colocadas como *tags*, que ajudam a que
te encontrem. O Etsy admite até 13, com um máximo de 20 caracteres cada, e podes
retocá-las antes de publicar.

## Começa a organizar o teu catálogo

Ter o catálogo bem organizado não é só uma questão de arrumação: é a forma de
saberes quanto te custa cada peça e quanto ganhas em cada encomenda, e de poderes
fazer crescer a tua oficina sem perder o controlo.

Se quiseres ver com mais detalhe como configurar o teu catálogo ou criar variantes
avançadas, dá uma vista de olhos à
[documentação do catálogo](/help/catalogo). E se te perguntas de onde vem o
custo de cada Peça, contamos-te em
[quanto custa realmente uma peça impressa](/blog/calculate-your-3d-printing-costs).

Descobre [como controlar a produção da tua oficina com o BolloPrint](/features), o
teu software para farms de impressão 3D.

Que o teu catálogo cresça tão organizado como começa.

![O Bollo, a mascote do BolloPrint, com óculos de oficina, junto ao seu modelo 3D em malha](/blog/media/2026-10-15-organizar-catalogo/07-bollo.webp "60%")

## Documentação relacionada

- [Catálogo](/help/catalogo): os níveis do catálogo, na referência
- [Designs](/help/disenos): os ficheiros, as fotos e as etiquetas
- [Peças](/help/piezas): o material, o ficheiro fatiado e o custo
- [Produtos e Variantes](/help/productos-y-variantes): o preço, a margem e as peças de cada variante
- [Criação rápida](/help/creacion-rapida): tudo de uma vez
- [Etiquetas](/help/etiquetas): como se criam e se gerem
