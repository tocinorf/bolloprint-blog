---
slug: connect-bambu-lab-printers-cloud
title: "Liga as tuas impressoras Bambu Lab ao BolloPrint em cinco minutos"
description: Sem instalar nada. Ligas a tua conta Bambu e as tuas máquinas aparecem sozinhas, com o que estão a imprimir e todo o seu histórico.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriais]
cover: 01-portada.webp
draft: true
---

Tens três Bambu a trabalhar e, para saberes como vão, levantas-te e vais ver o
ecrã de cada uma. A primeira já acabou? A segunda ainda tem material? Quantas
horas imprimiste este mês?

Há uma forma de ver tudo a partir de um só ecrã, e **não é preciso instalar
nada**. Ligas a tua conta Bambu Lab ao BolloPrint e as tuas máquinas aparecem
sozinhas. Cinco minutos.

::animation{id="bambu-cloud"}

## É isto que vais ter

De cada impressora, em direto e sem mexer em nada:

- se está ligada e com ligação;
- o que está a imprimir, a **percentagem** e o que lhe falta;
- as temperaturas do bico e da mesa;
- os **materiais** carregados, tabuleiro a tabuleiro, se tiveres AMS;
- os avisos da própria máquina.

E, além disso, o que realmente faz a diferença ao fim do mês: **cada impressão
fica registada**, com a sua duração, o seu material e o seu custo. Sem apontar
nada à mão.

![A ficha de uma impressora a imprimir, com o progresso e as temperaturas](/blog/media/2026-09-08-impresoras-por-la-nube/06-ficha-impresora.png "42%")

## O que precisas

- Entrar no BolloPrint como **Proprietário** ou **Admin**. Com outro papel, este
  ecrã não te aparece.
- A tua conta **Bambu Lab**, com o seu **email e a sua palavra-passe**.
- Poder abrir o **email** dessa conta: a Bambu vai enviar-te um código.

:::warning ⚠️ Se entras na Bambu com Google, Apple ou Facebook, isto não te vai funcionar
O BolloPrint precisa do **email e da palavra-passe** da tua conta Bambu. Se nunca
definiste uma palavra-passe porque carregas sempre em «Continuar com Google»,
cria-a primeiro no site da Bambu Lab e volta aqui com ela.
:::

## Passo 1 — Abre o ecrã das impressoras

Vai a **Configurações → Impressoras**. Vais ver três separadores:

- **Impressoras** — a lista de todas as tuas máquinas, venham por onde vierem.
- **Agente local** — para ligar pela tua rede. Isso é [outro tutorial](/blog/connect-printers-local-network-agent).
- **Bambu Cloud** — o que nos interessa hoje.

Abre **Bambu Cloud**.

![O ecrã Configurações → Impressoras com os seus três separadores](/blog/media/2026-09-08-impresoras-por-la-nube/02-tres-pestanas.png)

## Passo 2 — Escreve o teu email e a tua palavra-passe da Bambu

Os da tua conta Bambu Lab — esse email, não outro teu — e carrega em **Ligar à
BambuLab**.

![O formulário da Bambu Cloud, com o email da conta escrito e a palavra-passe ainda por pôr](/blog/media/2026-09-08-impresoras-por-la-nube/03-email-password.png)

:::info 💡 A tua palavra-passe não fica guardada
Fica **só no teu navegador**, e só até acabares de verificar.
:::

## Passo 3 — Introduz o código que te chega por email

A Bambu envia-te um **código de 6 dígitos** a partir de `noreply@bambulab.com`.
**Vê também no spam**: vai lá parar mais vezes do que devia.

Escreve os seis dígitos no mesmo ecrã e carrega em **Verificar e ligar**.

![O campo do código de 6 dígitos e o botão Verificar e ligar](/blog/media/2026-09-08-impresoras-por-la-nube/04-codigo-verificacion.png)

Dois pormenores que te poupam uma segunda tentativa: **o código expira ao fim de
uns 5 minutos** — se demorares, carrega em **Reenviar código** — e **cola-o
inteiro, tal como vier**: se trouxer espaços ou hífenes, são limpos sozinhos.

Quando for aceite, vais ver **Conta verificada e ligada**.

## Passo 4 — Já lá estão

Não é preciso registar as impressoras uma a uma. **Todas as máquinas dessa conta
aparecem sozinhas** no separador **Impressoras**, cada uma com o seu nome e o seu
número de série.

![A lista de impressoras com as máquinas da Bambu acabadas de aparecer](/blog/media/2026-09-08-impresoras-por-la-nube/05-impresoras-aparecidas.png)

Em cima há um contador do tipo `3 / 6 ativas`: as impressoras que o teu plano
inclui. Com o interruptor de cada linha ligas e desligas as que quiseres. Uma
desligada não conta para o limite, mas **continua na lista com todo o seu
histórico**.

E se ligares uma frota inteira e não houver lugares para todas, as que sobram
entram **desativadas**, em vez de te rebentarem com o plano.

## O que NÃO vais poder fazer por aqui

Mais vale sabê-lo agora do que andar meia hora à procura do botão:

- **É só de leitura.** Pela nuvem não se pode pausar, retomar nem cancelar a
  partir do BolloPrint: a Bambu só aceita essas ordens pela tua rede local, e com
  a impressora num modo especial. Vemos isso no fim.
- **Não há câmara.** Pela nuvem não chega. Chega, sim, a imagem do fatiamento do
  trabalho, que é a pré-visualização, não o que está a acontecer lá dentro.
- **Depende da internet duas vezes:** da tua e da da Bambu. Se qualquer uma
  falhar, a impressora aparece desligada, mesmo que esteja a imprimir
  perfeitamente.
- **A sessão expira de vez em quando** e é preciso voltar a ligar a conta.
  Avisamos-te no ecrã.

E uma que vale para todas as vias: **o BolloPrint não envia trabalhos para
imprimir**. O ficheiro continuas a enviá-lo a partir do teu fatiador. O que
fazemos é ler o que a máquina faz e registá-lo.

## Se não conseguires ligar

| O que vês | O que costuma ser |
|---|---|
| «Conta ou palavra-passe da Bambu Lab incorretas» e tens a certeza de que é a certa | **É a falha que mais tempo faz perder.** Se acabaste de criar essa palavra-passe e nunca a usaste, a conta tem o email por verificar e a Bambu não te diz nada. Entra **uma vez** no site da Bambu com essas credenciais, completa o que te for pedido e volta. |
| «Conta ou palavra-passe da Bambu Lab incorretas» e entras na Bambu com Google ou Apple | Essa via não serve aqui. Cria uma palavra-passe no site da Bambu. |
| «Não existe nenhuma conta da Bambu Lab com esse email» | O email não é o da conta Bambu. Vê com qual entras na app deles. |
| Fala-te de verificação em dois passos | Tens de a desativar na Bambu para poderes ligar a conta. |
| O código não chega | Vê no spam e carrega em **Reenviar código**. |
| Não aceita o código | Deve ter expirado. Pede outro e cola-o inteiro. |

## Queres mais? Experimenta o agente local

A nuvem mostra-te tudo, mas não te deixa mexer em nada, e só existe para a Bambu
Lab. Se queres mais, o que procuras é o **agente local**: um programa pequeno num
computador da tua oficina que fala com as impressoras pela tua própria rede. Um
chega para toda a frota, e dá-te:

- **quase todas as marcas**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron…;
- **câmara**, em direto enquanto a vês e com uma foto final guardada em cada
  impressão;
- **pausar, retomar e cancelar** a partir do BolloPrint, sem ires até à máquina;
- e **aguenta as falhas de internet**: continua a ler as tuas impressoras e
  conta-te tudo quando a ligação volta.

:::info 💡 Para enviar ordens a uma Bambu
A impressora tem de estar em **Modo LAN** e em **Modo programador**. Os dois
ativam-se no ecrã dela. Atenção: com o Modo LAN, a Bambu desliga-a da sua nuvem,
por isso, a partir daí, o BolloPrint vê-a pelo agente. Continua a ser **a mesma
impressora**, com o seu nome e todo o seu histórico, e ocupa **um só lugar** do
teu plano.
:::

Tens tudo passo a passo no próximo tutorial:
[ligar as tuas impressoras pela rede local](/blog/connect-printers-local-network-agent).

:::info 💡 Dúvidas?
Escreve-nos a partir da [página de contacto](/contact) ou abre um tópico no
[nosso Discord](/help/soporte-por-discord).
:::

## Documentação relacionada

- [Ligar impressoras](/help/conectar-impresoras) — as duas vias e qual te convém
- [Impressoras pela nuvem](/help/impresoras-por-la-nube) — a referência completa deste ecrã
- [Impressoras compatíveis](/help/impresoras-compatibles) — procura aqui o teu modelo
- [Tipos de ligação](/help/tipos-de-conexion) — o que cada família de impressora permite
