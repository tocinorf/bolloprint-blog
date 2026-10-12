---
slug: connect-printers-local-network-agent
title: "Liga as tuas impressoras pela tua própria rede: o agente local, passo a passo"
description: Prusa, Elegoo, Klipper, FlashForge, Bambu… Um agente pequeno num computador da oficina, toda a tua frota dentro do BolloPrint e sem mexer no router.
date: 2026-09-08
updated: 2026-10-12
tags: [tutoriais]
cover: 01-portada.webp
draft: true
---

As tuas impressoras estão na oficina. Tu, nem sempre. E sempre que queres saber
se uma continua a imprimir, se correu bem ou se ainda tem material, tens de estar
à frente dela.

Estarem na tua rede não quer dizer que tenhas de lá estar tu. Para isso existe o
**agente local**: um programa pequeno que vive num computador da tua oficina,
fala com as tuas impressoras pela tua própria rede e vai contando ao BolloPrint o
que vê.

- **Não mexes no router.** Nada de abrir portas, nem IP fixo, nem firewall.
- **Super leve.** Serve-lhe qualquer computador que já tenhas ligado.
- **Um para toda a frota**, por maior que seja.

::animation{id="local-agent"}

## Onde o pões

Em **qualquer computador da oficina que não desligues**: um NAS, um mini-PC, um
Raspberry Pi, o PC da oficina. Só lhe pedes duas coisas: que esteja **sempre
ligado** e que tenha **Docker**.

Melhor ainda se estiver **na mesma rede que as impressoras**, porque assim
encontra-as sozinho. Se não puder ser, adiciona-las à mão e funcionam exatamente
igual.

## Passo 1 — Cria-o no BolloPrint

Vai a **Configurações → Impressoras**, abre o separador **Agente local** e carrega
em **Novo agente**.

Dá-lhe um nome que ainda te diga alguma coisa daqui a seis meses. Um conselho:
**dá-lhe o nome do sítio onde está, não do que é**. «Rés do chão» ou «Pavilhão 2»
servem; «Agente 1», não.

![O separador Agente local, com o botão Novo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Passo 2 — Copia o manifesto

Ao criá-lo, o BolloPrint mostra-te um **manifesto**: um texto que já traz lá
dentro tudo o que é teu — as chaves do teu agente e a versão certa — **já
escrito**. Não há nada para substituir nem para preencher.

Escolhe o formato que usas (**Docker Compose** é o normal) e carrega em
**Copiar**.

![O manifesto de instalação, com o botão de copiar](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Copia-o agora: só é mostrado uma vez
As chaves não expiram, mas não voltamos a mostrá-las. Se perderes o manifesto,
não é nada de grave: abres o agente e usas **Regenerar chaves** para obteres um
novo.
:::

## Passo 3 — Cola-o onde o vais arrancar

Isto já é no teu computador, não no BolloPrint. Depende de onde o puseres:

**Num NAS Synology.** Instala o **Container Manager** a partir do **Centro de
Pacotes**. Vai a **Projeto → Criar**, cola o manifesto e carrega em criar. Sem
escrever um único comando.

**Em Windows ou Mac.** Instala o **Docker Desktop**, guarda o manifesto numa
pasta como `docker-compose.yml` e arranca-o a partir dessa pasta com
`docker compose up -d`.

**Em Linux.** Instala o **Docker** com o gestor de pacotes da tua distribuição,
guarda o manifesto como `docker-compose.yml` e, a partir dessa pasta,
`docker compose up -d`.

Usas o **Portainer**? Colas o mesmo manifesto numa stack e fazes deploy.

:::info 💡 Em Windows e Mac, as impressoras não são encontradas sozinhas
Aí o Docker corre dentro de uma máquina virtual, que não vê os anúncios que as
impressoras enviam para a tua rede. O agente funciona igual, mas as impressoras
adiciona-las tu, como no passo 6.
:::

## Passo 4 — Confirma que está online

Volta ao BolloPrint. Em menos de um minuto, o agente passa a **Online**.

![O agente no estado Online](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Se não aparecer, é quase sempre uma destas três coisas: o manifesto **colado só
em parte**, o computador **sem internet**, ou uma **firewall** a bloquear a saída.

## Passo 5 — As tuas impressoras aparecem sozinhas

O agente **procura impressoras na tua rede** por conta própria, a cada 15
minutos. As que encontra aparecem numa lista com a sua marca e o seu modelo, e tu
decides:

- **Adicionar** — registas a impressora e ela começa a reportar.
- **Ignorar** — não é tua, ou não a queres aqui.

![As impressoras encontradas na rede, com os botões de adicionar e ignorar](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Se acabaste de ligar uma máquina e não queres esperar, há um botão **Procurar
agora**.

Algumas vão pedir-te uma **palavra-passe** ao adicioná-las. Depende da marca, e
vemos isso já a seguir.

## Passo 6 — Se alguma não aparecer, adiciona-la tu

É **normal** uma impressora não aparecer sozinha em dois casos:

- **Está noutra rede.** Os anúncios das impressoras não passam de uma rede para
  outra, por isso não são encontradas sozinhas.
- **O agente corre em Windows ou Mac.** Aí o Docker corre numa máquina virtual,
  e também não são encontradas sozinhas.

**Não perdes nada com isso.** Adiciona-la tu e funciona exatamente igual, com
câmara e com comandos, se essa máquina os tiver. Carregas em **Adicionar por IP**
e indicas o tipo de impressora, o seu endereço na tua rede e, se a pedir, a sua
palavra-passe.

![O formulário para adicionar uma impressora pelo seu IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Reserva-lhe o IP no router
Se o router mudar o endereço de uma impressora, voltamos a encontrá-la sozinhos,
mas vai estar em baixo durante um bocado. Reservar-lhe o endereço evita essa
falha. É uma configuração do router, não do BolloPrint.
:::

## O que cada marca te pede

É aqui que as pessoas se atrapalham. Resumimos:

| Marca | O que tens de fazer na máquina | Câmara | Podes pausar e cancelar? |
|---|---|---|---|
| **Bambu Lab** | Ativar o **Modo LAN** no ecrã dela e usar o **código de acesso** que te mostra | Sim | Sim, se também ativares o **Modo programador** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Usar a **palavra-passe** que a própria impressora mostra | Ainda não | Sim |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Normalmente nada: costuma ligar-se sem palavra-passe | Sim, se tiveres webcam no teu Klipper | Sim |
| **Elegoo de resina** (Mars, Saturn, Jupiter) | Nada, não pede palavra-passe | Nos modelos que a trazem | Sim |
| **Elegoo Centauri Carbon 2** | Só se lhe puseste um código no ecrã | Sim | Ainda não |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Ativar **LAN Only** e usar o código do ecrã | Sim | Ainda não |

:::warning ⚠️ Bambu Lab: o código de acesso MUDA
Sempre que ativas ou desativas o Modo LAN, a Bambu **gera um código novo**. Se
uma Bambu que funcionava bem deixa de repente de ligar, em nove de cada dez vezes
é isto: vê outra vez o código no ecrã dela e atualiza-o no BolloPrint.
:::

:::info 💡 Não encontras o teu modelo na tabela?
Vê em [impressoras compatíveis](/help/impresoras-compatibles). E se tiver
**Klipper** lá dentro — qualquer máquina montada por ti ou modificada — entra,
mesmo que a marca não apareça em nenhuma lista.
:::

## Se já tinhas Bambu pela nuvem, não as dupliques

Quando o agente encontra na tua rede uma máquina que **já tinhas ligada pela
nuvem**, o BolloPrint deteta-o e diz-te: *«É "P1S-02", que já tens pela Bambu
Cloud»*. O botão é **Ligar também por LAN**.

Carrega nele, e não a vais ter duas vezes:

- Continua a ser **uma só impressora**, com o seu número, o seu nome e todo o seu
  histórico.
- Ocupa **um só lugar** do teu plano.
- E ganha a **câmara**, que é o que não tinhas pela nuvem.

![O aviso de que essa impressora já está na Bambu Cloud, com o botão de ligar também por LAN](/blog/media/2026-09-08-impresoras-red-local-agente/07-tambien-por-lan.png)

:::warning ⚠️ O Modo LAN desliga a nuvem da Bambu
Ao ativá-lo, a impressora deixa de falar com a nuvem da Bambu Lab. A partir daí,
o BolloPrint vê-a pelo agente.
:::

## O que ganhas, em concreto

- **Quase todas as marcas.** Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron… Isto a nuvem não te dá, porque só existe para a Bambu Lab.
- **Câmara.** Vê-la em direto enquanto tens a página à frente, tirar uma foto
  quando quiseres, e uma foto final guardada no histórico de cada impressão. Não
  é videovigilância: não se grava nada.
- **Comandos.** Pausar, retomar e cancelar a partir do BolloPrint, sem ires até à
  máquina, nas que o permitem (vê a tabela acima). Na Bambu Lab, com a impressora
  em **Modo LAN** e **Modo programador**.
- **Aguenta as falhas de internet.** Se a tua ligação cair, o agente **continua a
  ler as impressoras e guarda o que se passa**. Quando a ligação volta, envia
  tudo. Não perdes essas horas de histórico.
- **Não dependes do fabricante** nem de que a nuvem dele continue a funcionar.

O que não se pode fazer por nenhuma via: **enviar trabalhos para imprimir**. O
ficheiro continuas a enviá-lo a partir do teu fatiador.

## Perguntas que nos fazem muito

**Tenho de abrir portas no router?** Não. Nem portas, nem IP fixo, nem regras de
firewall. Funciona atrás de um router doméstico normal.

**É preciso um agente por impressora?** Não. **Um só leva a frota inteira.** Só
faz sentido ter vários se tiveres dois espaços ou duas redes separadas.

**E se desligar o computador, ou sair uma versão nova?** Quando o voltares a
ligar, o agente volta sozinho. E atualiza-se sozinho: quando sai uma versão nova,
descarrega-a e reinicia com ela. Só terás de fazer alguma coisa se te avisarmos
no ecrã.

:::info 💡 Ficaste encravado?
Escreve-nos a partir da [página de contacto](/contact) ou abre um tópico no
[nosso Discord](/help/soporte-por-discord). Se nos disseres que impressoras tens,
dizemos-te exatamente o que fazer com cada uma.
:::

## Documentação relacionada

- [Ligar impressoras](/help/conectar-impresoras) — as duas vias e qual te convém
- [O agente local](/help/el-agente-local) — a referência completa
- [Instalar o agente](/help/desplegar-el-agente) — o detalhe técnico, se precisares
- [Tipos de ligação](/help/tipos-de-conexion) — o que cada família de impressora permite
- [Impressoras compatíveis](/help/impresoras-compatibles) — procura aqui o teu modelo
