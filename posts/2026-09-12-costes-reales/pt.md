---
slug: calculate-your-3d-printing-costs
title: "Quanto custa realmente uma peça impressa (e como calculá-lo sem complicações)"
description: Essa peça de 1,60 € de filamento custa-te 9,36 €. Mostramos-te como repartir as despesas da tua oficina pelas tuas horas de impressão para que o BolloPrint o aplique sozinho a cada peça.
date: 2026-10-15
tags: [tutoriais]
cover: 01-portada.webp
---

Uma peça de 6 horas e 80 gramas de PLA. Quanto te custa?

Se pensaste «80 gramas a 20 € o quilo, **1,60 €**», calculaste apenas o
**material**. Numa oficina normal, isso é **uma parte pequena** do que a peça
realmente te custa.

Numa oficina de três impressoras, com a peça pintada e embalada, a conta
completa é esta:

| | |
|---|---|
| Material | 1,60 € |
| 6 horas de impressora | 5,16 € |
| Acabamento (pintada) | 2,00 € |
| Custos extra (embalagem) | 0,60 € |
| **Custo real da peça** | **9,36 €** |

**Quase seis vezes mais.** A diferença não é um arredondamento: é a renda, a luz,
o desgaste das impressoras, o contabilista e as peças que saem mal. Tudo isso
pagas tu; a questão é se o estás a cobrar.

Aqui vais ver como levar essas despesas ao custo de cada peça. **Configura-se uma
vez** e depois aplica-se sozinho a cada peça que criares.

::animation{id="part-cost"}

## De onde vêm esses 5,16 €

A ideia é simples: somas **tudo o que a oficina te custa por mês** e divides
pelas **horas em que imprimes de verdade**. Assim obténs quanto te custa **uma
hora de impressora**, e só falta multiplicá-lo pelas horas da peça.

Com os números do exemplo:

- **Horas:** três impressoras, dez horas por dia, vinte e cinco dias por mês →
  **750 horas**.
- **Despesas:** entre renda, contabilista, software e a amortização das
  máquinas, vão-se uns **516 € por mês**. Repartido: 0,69 € por hora. Com a luz,
  o **custo base** fica em **0,72 €**.
- **Acréscimos:** 5 % de manutenção, 10 % de taxa de falhas e 5 % de imprevistos
  levam-no a **0,86 € por hora**. Por seis horas, 5,16 €.

É exatamente esta a conta que faz a secção **Custos** do BolloPrint, em
**Configurações → Custos**. Só a veem o **Proprietário** e os **Admins**.

![A secção Custos dentro das Configurações](/blog/media/2026-09-12-costes-reales/02-seccion-costes.png)

## As horas em que imprimes de verdade

Começa pelas horas: é o número que mais gente calcula mal, e o que mais muda o
resultado. Está em **Custo por hora → Horas de impressão**, e são três campos:

**Impressoras × Horas por dia × Dias por mês**

Põe **o que acontece de verdade, não o máximo teórico**. Se tens três impressoras
mas, em média, trabalham oito horas por dia, são oito. Não vinte e quatro.

É tentador pôr um número alto, porque quanto mais alto, mais barata sai a hora.
Mas essas despesas pagas na mesma, e o que não repartires pelas peças acabas por
ser tu a pagá-lo ao fim do mês.

![O separador Horas de impressão, com os três campos e o resultado](/blog/media/2026-09-12-costes-reales/03-horas-impresion.png)

## O que te custa a oficina

Definidas as horas, passa às despesas. Em **Custo base** vais acrescentando-as;
o BolloPrint ordena-as por tipo e pede-te de cada uma só o que precisa:

| Tipo | O que lhe pões |
|---|---|
| **Custo fixo** | Renda, internet, contabilista, seguros… o valor por mês |
| **Impressora** | Quanto te custou e em quantos anos a amortizas |
| **Software** | A subscrição do fatiador, do BolloPrint, do que usares |
| **Salários** | O salário e quantas pessoas |
| **Eletricidade** | Os kW que uma impressora consome e quanto te cobram pelo kWh |

Não é preciso que seja exato ao cêntimo: vale mais um número razoável hoje do que
o número perfeito no ano que vem.

:::warning ⚠️ Não ponhas a mesma despesa duas vezes
Os valores **por mês** descrevem **toda a oficina**: a renda põe-se uma única
vez. Os que vão **por hora impressa** — como a eletricidade por consumo —
descrevem **uma única impressora**: aí põe o consumo de uma máquina média, não o
de todo o pavilhão.
:::

Lá em baixo tens a conta feita, a mesma do início:

> **despesas do mês ÷ as tuas horas de impressão = o que te custa uma hora «a limpo»**

Isso é o **custo base por hora**: 0,72 € no exemplo.

![As despesas da oficina em Custo base, agrupadas por tipo, e a conta que dá 0,72 € por hora](/blog/media/2026-09-12-costes-reales/03b-coste-base.png)

## O que sabes que vai acontecer

O custo base deixa de fora o que acontece sem fatura fixa: partem-se bicos, e
**alguma peça sai mal e tem de ser repetida**.

Para isso existe o **Custo total**, que soma umas percentagens ao custo base:
manutenção, taxa de falhas e imprevistos.

A taxa de falhas é a mais importante, e a que mais gente salta. Se em cada dez
peças uma vai para o lixo, **as nove boas estão a pagar a má**. Se não a incluíres
aqui, pagas tu.

O resultado é o teu **custo total por hora**: 0,86 € no exemplo. Esse é o teu
número a sério, e é o que se aplica a cada peça.

:::info 💡 A margem de lucro não vai aqui
Aqui só vão **custos**. Quanto queres ganhar decide-se depois, no produto, porque
é uma decisão comercial.
:::

![Os acréscimos de manutenção, taxa de falhas e imprevistos sobre o custo base, até 0,86 € por hora](/blog/media/2026-09-12-costes-reales/03c-coste-total.png)

## O material e os extras

Fica a parte mais simples, em **Valores por omissão**:

- **O preço de cada material**, por quilo. É **por tipo**, não por família: o
  PLA e o TPU não custam o mesmo.
- **Os acabamentos**: quanto acrescentas se a peça for pós-processada ou pintada.
- **Os custos extra**: embalagem, parafusaria, ímanes, insertos, mão de obra.
  Para cada um escolhes se se cobra **por unidade** ou **por placa**.
- **As margens**: a que queres por omissão, e a partir de que percentagem te
  avisamos a vermelho ou a laranja.

:::info 💡 Se tens o material no inventário, manda o inventário
Estes preços são de referência, para quando não há nada por trás. Se a peça sair
de uma bobina registada com o seu custo real, usamos esse.
:::

![Valores por omissão: as margens com os avisos de cor e o preço de cada material por quilo](/blog/media/2026-09-12-costes-reales/03d-valores-por-defecto.png)

## E é assim que chega à tua peça

Os quatro passos anteriores acabam num só número: **o que te custa uma hora de
impressora**. A partir daí, cada peça é uma soma:

> as suas **horas × o teu custo por hora**
> **+** o **material** que leva
> **+** o **acabamento**, se for pós-processada ou pintada
> **+** os **custos extra** que lhe acrescentares

Há um pormenor que convém perceber, porque explica por que vale a pena encher a
mesa: **a conta faz-se por placa, não por peça**. O BolloPrint calcula o que
custa a placa inteira e **reparte-o pelas peças que saem dela**. Por isso, dos
custos extra, os que marcas **por placa** cobram-se uma só vez — quer imprimas as
peças de uma em uma quer de vinte em vinte — e os **por unidade** cobram-se em
cada peça.

Além disso, cada peça **guarda o custo por hora com que foi calculada**. É de
propósito: assim, o custo do que imprimiste no ano passado continua a ser o de
então. É por isso que existe o botão **Recalcular**, um pouco mais abaixo.

## Agora já tens o teu número

Para ver o resultado, vai a **Custos → Resumo**. O bloco **Exemplo** pega numa
placa de amostra e mostra-te a conta inteira **com os teus valores**: quanto é
material, quanto é impressão, quanto é acabamento e quanto fica a peça.

![O bloco Exemplo com a decomposição completa de uma peça](/blog/media/2026-09-12-costes-reales/04-ejemplo-coste.png)

## Quando as tuas despesas mudarem

Os teus números não vão ser sempre os mesmos: sobe a luz, compras outra
impressora ou mudas de espaço. Quando os atualizas, **as peças que já tinhas não
mudam sozinhas**. É de propósito: cada peça guarda o custo com que foi calculada,
e não ias querer que se reescrevesse o de tudo o que fizeste no ano passado.

Quando o quiseres aplicar a tudo, em **Resumo** tens um contador de peças **por
recalcular** e o botão **Recalcular**. Tu decides quando.

:::info 💡 Não mexe nos teus preços de venda
Recalcular atualiza o **custo** e o preço *sugerido*. O que tiveres posto à mão
fica como está. O que vais ver mexer-se é o indicador de **margem**.
:::

## Compro outra impressora?

Com os teus custos configurados, podes responder a esta pergunta com números. No
**Comparador de farm** mexes nas impressoras, nas horas ou nos dias e vês o que
aconteceria ao teu custo por hora. Só simula: não muda nada da tua configuração.

O que mostra melhor é que **a curva deixa de descer**. Passar de uma impressora
para cinco divide o custo por hora quase por cinco. Passar de vinte para cem quase
não o mexe, porque há despesas — como a luz — que se pagam em cada hora impressa
e não se repartem por ninguém.

![O comparador de farm, com a curva do custo por hora](/blog/media/2026-09-12-costes-reales/05-comparador.png)

Configurá-lo são quatro ecrãs e um bocado de uma tarde. Em troca, cada peça que
criares vai levar o seu custo real, e vais saber se estás a ganhar dinheiro sem
fazer a conta à mão.

:::info 💡 Ajudamos-te com os teus números?
Se não sabes por onde começar, escreve-nos a partir da [página de contacto](/contact)
ou no [nosso Discord](/help/soporte-por-discord). Já o fizemos umas quantas vezes.
:::

Que as tuas contas batam sempre certo.

![O Bollo, a mascote do BolloPrint, com óculos de oficina, pensativo entre contas escritas a giz](/blog/media/2026-09-12-costes-reales/07-bollo.webp "60%")

## Documentação relacionada

- [Custos](/help/costes): a referência completa da secção
- [Peças](/help/piezas): como se calcula o custo de cada peça
- [Produtos e Variantes](/help/productos-y-variantes): do custo ao preço de venda
- [Inventário](/help/inventario): para que o material saia do seu custo real
