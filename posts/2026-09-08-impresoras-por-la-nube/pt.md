---
slug: connect-bambu-lab-printers-cloud
title: "Liga as tuas impressoras Bambu Lab ao BolloPrint em cinco minutos"
description: Sem instalar nada e sem palavra-passe. Escreves o email da tua conta Bambu Lab, confirmas um código e as tuas impressoras aparecem sozinhas, com o que estão a imprimir e todo o seu histórico.
date: 2026-10-12
updated: 2026-10-14
tags: [tutoriais]
cover: 01-portada.webp
---

Se tens várias Bambu a trabalhar, provavelmente conheces a rotina: para saberes
como vão, vais até cada uma e olhas para o ecrã. A primeira já acabou? A segunda
ainda tem material? Quantas horas imprimiste este mês?

Podes ter tudo isso num só ecrã e **sem instalar nada**. Ligas a tua conta Bambu
Lab ao BolloPrint e as tuas impressoras aparecem sozinhas. São cerca de cinco
minutos.

::animation{id="bambu-cloud"}

## O que vais ver de cada impressora

Em tempo real e sem mexer em nada:

- se está ligada e com ligação;
- o que está a imprimir, a **percentagem** que já leva e o que lhe falta;
- as temperaturas do bico e da mesa;
- os **materiais** carregados, tabuleiro a tabuleiro, se tiveres AMS;
- os avisos da própria máquina.

E o que mais se nota ao fim do mês: **cada impressão fica registada**, com a sua
duração, o seu material e o seu custo. Não tens de apontar nada.

![A ficha de uma impressora a imprimir, com o progresso e as temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora-pt.png "42%")

## O que precisas

Antes de começares, tem à mão estas três coisas:

- Acesso ao BolloPrint como **Proprietário** ou **Admin**. Com outro papel, este
  ecrã não aparece.
- O **email** da tua conta Bambu Lab. A palavra-passe não é precisa.
- Esse **email** aberto: a Bambu vai enviar-te um código.

## Abre o ecrã das impressoras

Tudo se faz no mesmo sítio: **Configurações → Impressoras**. Aí vais ver três
separadores:

- **Impressoras**: a lista de todas as tuas máquinas, venham por onde vierem.
- **Agente local**: para as ligar pela tua própria rede. Explicamo-lo
  [noutro artigo](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: o que precisas agora.

Abre **Bambu Cloud**.

![O ecrã Configurações → Impressoras com os seus três separadores](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas-pt.png)

## Escreve o email da tua conta Bambu

Usa o da tua conta Bambu Lab (esse email, não outro teu) e carrega em **Enviar
código**.

![O formulário da Bambu Cloud, com o email da conta escrito e o botão Enviar código](/blog/media/2026-09-08-impresoras-por-la-nube/03-correo-pt.png)

:::info 💡 Não te pedimos a palavra-passe
O BolloPrint **nunca a vê nem a guarda**: para ligar, basta o código que a Bambu
te envia por email.
:::

## Confirma o código do email

A Bambu vai enviar-te um **código de 6 dígitos** a partir de
`noreply@bambulab.com` (o email chega em inglês). Se não o vires, **verifica a pasta de spam**: costuma ir
lá parar. Escreve-o no mesmo ecrã e carrega em **Verificar e ligar**.

![O campo do código de 6 dígitos e o botão Verificar e ligar](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-pt.png)

Três pormenores poupam-te uma segunda tentativa:

- O código **expira ao fim de 10 minutos** e só vale o último. Se o prazo
  passar, carrega em **Reenviar código**.
- Podes **colá-lo tal como chega**: os espaços ou hífenes são removidos
  automaticamente.
- Se te enganaste no email, carrega em **Mudar de email**.

Quando for aceite, vais ver **Conta verificada e ligada**.

## As tuas impressoras já lá estão

Não é preciso registá-las uma a uma: **todas as impressoras dessa conta aparecem
sozinhas** no separador **Impressoras**, cada uma com o seu nome e o seu número
de série.

![A lista de impressoras com as máquinas da Bambu acabadas de aparecer](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas-pt.png)

Em cima vais ver um contador do tipo `3 / 6 ativas`: são as impressoras que o
teu plano inclui. Com o interruptor de cada linha ativas ou desativas as que
quiseres. Uma impressora desativada não conta para o limite, mas **mantém todo o
seu histórico**. E se ligares uma frota inteira e não houver lugares para todas,
as que não cabem entram desativadas, em vez de ultrapassarem o limite do teu plano.

## O que não podes fazer pela nuvem

Convém sabê-lo desde o início, para não procurares opções que não existem:

- **É só de leitura.** Pela nuvem não se pode pausar, retomar nem cancelar a
  partir do BolloPrint: a Bambu só aceita essas ordens pela tua rede local e com
  a impressora num modo específico. Vemos isso no fim.
- **Não há câmara.** Vês, sim, a imagem do fatiamento do trabalho, que é uma
  pré-visualização, não o que acontece dentro da máquina.
- **Depende de duas ligações à internet**, a tua e a da Bambu. Se qualquer uma
  falhar, a impressora aparece desligada, mesmo que esteja a imprimir
  normalmente.
- **A sessão com a Bambu dura 90 dias, mas renova-se sozinha**: o BolloPrint
  renova-a antes de expirar e não tens de voltar a entrar. Só se a Bambu a
  fechar por iniciativa própria te avisamos no ecrã, e basta pedir um código
  novo.

E algo que vale para qualquer forma de ligação: **o BolloPrint não envia
trabalhos para imprimir**. O ficheiro continuas a enviá-lo a partir do teu
fatiador; o BolloPrint lê o que a máquina faz e regista-o.

## Problemas frequentes

### E se entrares na Bambu com Google ou Apple?

Escreve o email dessa conta Google ou Apple: o código chega lá na mesma. Já não
é preciso criar uma palavra-passe.

### Porque é que diz que não existe uma conta com esse email?

Se aparecer **«Não existe nenhuma conta da Bambu Lab com esse email.»**, o email
não é o da tua conta Bambu: a Bambu envia o código na mesma, mas rejeita-o quando
o escreves. Confirma com qual entras na app deles e carrega em **Mudar de
email**.

### Tenho de voltar a ligar a conta de tempos a tempos?

Não. A sessão dura 90 dias e o BolloPrint renova-a sozinho antes de expirar. Se
alguma vez a Bambu a fechar por iniciativa própria, vais ver **«Sessão
expirada»** e um botão **Voltar a iniciar sessão**: pedes um código novo e
pronto, sem desvincular nada.

### O que faço se o código não chegar ou não for aceite?

Se não chegar, verifica a pasta de spam e carrega em **Reenviar código**. Se não
for aceite, o mais provável é que tenha expirado ou que não seja o último que
pediste: pede outro e cola-o inteiro.

## Se precisares de mais: o agente local

A nuvem mostra-te toda a informação, mas não te permite atuar sobre as
impressoras, e só existe para a Bambu Lab. Se precisares de mais, a opção é o
**agente local**: um programa pequeno que instalas num computador da tua oficina
e que comunica com as impressoras pela tua própria rede. Um chega para toda a
frota, e dá-te:

- **quase todas as marcas**: Prusa, Elegoo, Anycubic, FlashForge, Snapmaker e
  todas as que têm Klipper (QIDI, Sovol, Voron…);
- **câmara**, em direto e com uma foto final guardada em cada impressão;
- **pausar, retomar e cancelar** a partir do BolloPrint, sem ires até à máquina;
- **resistência às falhas de internet**: continua a ler as tuas impressoras e
  envia tudo quando a ligação volta.

:::info 💡 Para enviar ordens a uma Bambu
A impressora tem de estar em **Modo LAN** e em **Modo programador**. Os dois
ativam-se no ecrã dela, e o segundo desliga-a da Bambu Cloud: a partir daí só a
vês através do agente.
:::

Explicamos tudo passo a passo em
[liga as tuas impressoras pela tua própria rede](/blog/connect-printers-local-network-agent).

Se tiveres alguma dúvida, escreve-nos a partir da [página de contacto](/contact)
ou no [nosso Discord](/help/soporte-por-discord).

Bom trabalho com todas as tuas impressoras num só ecrã.

![O Bollo, a mascote do BolloPrint, com óculos de oficina, a sonhar com uma impressora 3D](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp "60%")

## Documentação relacionada

- [Ligar impressoras](/help/conectar-impresoras): as duas formas de o fazer e qual te convém
- [Impressoras pela nuvem](/help/impresoras-por-la-nube): a referência completa deste ecrã
- [Impressoras compatíveis](/help/impresoras-compatibles): procura aqui o teu modelo
- [Tipos de ligação](/help/tipos-de-conexion): o que cada tipo de impressora permite
