---
slug: connect-bambu-lab-printers-cloud
title: "Liga as tuas impressoras Bambu Lab ao BolloPrint em cinco minutos"
description: Sem instalar nada. Ligas a tua conta Bambu Lab, confirmas um código e as tuas impressoras aparecem sozinhas, com o que estão a imprimir e todo o seu histórico.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriais]
cover: 01-portada.webp
draft: true
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

![A ficha de uma impressora a imprimir, com o progresso e as temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## O que precisas

Antes de começares, tem à mão estas três coisas:

- Acesso ao BolloPrint como **Proprietário** ou **Admin**. Com outro papel, este
  ecrã não aparece.
- O **email e a palavra-passe** da tua conta Bambu Lab.
- O **email** dessa conta aberto: a Bambu vai enviar-te um código.

:::warning ⚠️ Se entras na Bambu com Google, Apple ou Facebook
O BolloPrint precisa do **email e da palavra-passe** da conta. Se nunca definiste
uma palavra-passe porque usas sempre «Continuar com Google», cria-a primeiro no
site da Bambu Lab e volta depois.
:::

## Abre o ecrã das impressoras

Tudo se faz no mesmo sítio: **Configurações → Impressoras**. Aí vais ver três
separadores:

- **Impressoras**: a lista de todas as tuas máquinas, venham por onde vierem.
- **Agente local**: para as ligar pela tua própria rede. Explicamo-lo
  [noutro artigo](/blog/connect-printers-local-network-agent).
- **Bambu Cloud**: o que precisas agora.

Abre **Bambu Cloud**.

![O ecrã Configurações → Impressoras com os seus três separadores](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Escreve o email e a palavra-passe da Bambu

Usa os da tua conta Bambu Lab (esse email, não outro teu) e carrega em **Ligar à
BambuLab**.

![O formulário da Bambu Cloud, com o email da conta escrito e a palavra-passe ainda por pôr](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 A tua palavra-passe não fica guardada
Fica **só no teu navegador**, e só até acabares a verificação.
:::

## Confirma o código do email

A Bambu vai enviar-te um **código de 6 dígitos** a partir de
`noreply@bambulab.com`. Se não o vires, **verifica a pasta de spam**: costuma ir
lá parar. Escreve-o no mesmo ecrã e carrega em **Verificar e ligar**.

![O campo do código de 6 dígitos e o botão Verificar e ligar](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Dois pormenores poupam-te uma segunda tentativa:

- O código **expira ao fim de uns 5 minutos**. Se o prazo passar, carrega em
  **Reenviar código**.
- Podes **colá-lo tal como chega**: os espaços ou hífenes são removidos
  automaticamente.

Quando for aceite, vais ver **Conta verificada e ligada**.

## As tuas impressoras já lá estão

Não é preciso registá-las uma a uma: **todas as impressoras dessa conta aparecem
sozinhas** no separador **Impressoras**, cada uma com o seu nome e o seu número
de série.

![A lista de impressoras com as máquinas da Bambu acabadas de aparecer](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

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
- **A sessão expira de vez em quando** e é preciso voltar a ligar a conta.
  Avisamos-te no ecrã.

E algo que vale para qualquer forma de ligação: **o BolloPrint não envia
trabalhos para imprimir**. O ficheiro continuas a enviá-lo a partir do teu
fatiador; o BolloPrint lê o que a máquina faz e regista-o.

## Problemas frequentes

### Porque é que a Bambu diz que a palavra-passe está errada se é a certa?

É o problema mais habitual. A mensagem **«Conta ou palavra-passe da Bambu Lab
incorretas»** aparece quase sempre com uma palavra-passe acabada de criar que
ainda não foi usada: a conta tem o email por verificar e a Bambu não o indica.
Entra **uma vez** no site da Bambu com esse email e essa palavra-passe, completa
o que te for pedido e tenta de novo.

### E se entrares na Bambu com Google ou Apple?

Por essa via não é possível. Cria uma palavra-passe no site da Bambu Lab e usa o
email com essa palavra-passe.

### Porque é que diz que não existe uma conta com esse email?

Se aparecer **«Não existe nenhuma conta da Bambu Lab com esse email»**, o email
não é o da tua conta Bambu. Confirma com qual entras na app deles.

### O que faço se me pedir verificação em dois passos?

Vais ter de a desativar na tua conta Bambu para a poderes ligar.

### O que faço se o código não chegar ou não for aceite?

Se não chegar, verifica a pasta de spam e carrega em **Reenviar código**. Se não
for aceite, o mais provável é que tenha expirado: pede outro e cola-o inteiro.

## Se precisares de mais: o agente local

A nuvem mostra-te toda a informação, mas não te permite atuar sobre as
impressoras, e só existe para a Bambu Lab. Se precisares de mais, a opção é o
**agente local**: um programa pequeno que instalas num computador da tua oficina
e que comunica com as impressoras pela tua própria rede. Um chega para toda a
frota, e dá-te:

- **quase todas as marcas**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron…;
- **câmara**, em direto e com uma foto final guardada em cada impressão;
- **pausar, retomar e cancelar** a partir do BolloPrint, sem ires até à máquina;
- **resistência às falhas de internet**: continua a ler as tuas impressoras e
  envia tudo quando a ligação volta.

:::info 💡 Para enviar ordens a uma Bambu
A impressora tem de estar em **Modo LAN** e em **Modo programador**. Os dois
ativam-se no ecrã dela.
:::

Explicamos tudo passo a passo em
[liga as tuas impressoras pela tua própria rede](/blog/connect-printers-local-network-agent).

Se tiveres alguma dúvida, escreve-nos a partir da [página de contacto](/contact)
ou no [nosso Discord](/help/soporte-por-discord).

Bom trabalho com todas as tuas impressoras num só ecrã.

![O Bollo, a mascote do BolloPrint, com óculos de oficina, a sonhar com uma impressora 3D](/blog/media/2026-09-08-impresoras-por-la-nube/07-bollo.webp)

## Documentação relacionada

- [Ligar impressoras](/help/conectar-impresoras): as duas formas de o fazer e qual te convém
- [Impressoras pela nuvem](/help/impresoras-por-la-nube): a referência completa deste ecrã
- [Impressoras compatíveis](/help/impresoras-compatibles): procura aqui o teu modelo
- [Tipos de ligação](/help/tipos-de-conexion): o que cada tipo de impressora permite
