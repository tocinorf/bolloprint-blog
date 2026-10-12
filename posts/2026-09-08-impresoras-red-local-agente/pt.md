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

As tuas impressoras estão na oficina, mas tu nem sempre. E para saberes se uma
continua a imprimir, se correu bem ou se ainda tem material, tens de estar à
frente dela.

Para isso existe o **agente local**: um programa pequeno que corre num computador
da tua oficina, fala com as tuas impressoras pela tua própria rede e comunica ao
BolloPrint o que vê.

- **Não mexes no router**: nada de portas abertas, nem IP fixo, nem firewall.
- **É muito leve**: serve-lhe qualquer computador que já tenhas ligado.
- **Basta um para toda a frota**, seja qual for o tamanho.

::animation{id="local-agent"}

## Onde o instalar

O agente vive em **qualquer computador da oficina que não desligues**: um NAS, um
mini-PC, um Raspberry Pi ou o PC da oficina. Só precisa de estar **sempre ligado**
e de ter **Docker**.

O ideal é que esteja **na mesma rede que as impressoras**, porque assim
encontra-as sozinho. Se não for possível, adiciona-las à mão e funcionam igual.

## Cria o agente no BolloPrint

Começa no BolloPrint. Vai a **Configurações → Impressoras**, abre o separador
**Agente local** e carrega em **Novo agente**.

Dá-lhe um nome que ainda te diga alguma coisa daqui a seis meses: **dá-lhe o nome
do sítio onde está, não do que é**. «Rés do chão» ou «Pavilhão 2» servem;
«Agente 1», não.

![O separador Agente local, com o botão Novo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente.png)

## Copia o manifesto

Ao criá-lo, o BolloPrint mostra-te um **manifesto**: um texto que já traz
**escrito** tudo o que é teu, as chaves do teu agente e a versão certa. Não há
nada para substituir nem para preencher.

Escolhe o formato que usas (**Docker Compose** é o habitual) e carrega em
**Copiar**.

![O manifesto de instalação, com o botão de copiar](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla.png)

:::warning 🔐 Copia-o agora: só é mostrado uma vez
As chaves não expiram, mas não voltamos a mostrá-las. Se perderes o manifesto,
abre o agente e usa **Regenerar chaves** para obteres um novo.
:::

## Cola o manifesto no teu computador

Isto já é no teu computador, não no BolloPrint, e depende de onde o instalares:

- **NAS Synology**: instala o **Container Manager** a partir do **Centro de
  Pacotes**, vai a **Projeto → Criar**, cola o manifesto e cria o projeto. Sem
  escrever nenhum comando.
- **Windows ou Mac**: instala o **Docker Desktop**, guarda o manifesto numa pasta
  como `docker-compose.yml` e, a partir dessa pasta, executa
  `docker compose up -d`.
- **Linux**: instala o **Docker** com o gestor de pacotes da tua distribuição,
  guarda o manifesto como `docker-compose.yml` e executa aí
  `docker compose up -d`.
- **Portainer**: cola o mesmo manifesto numa stack e faz deploy.

:::info 💡 Em Windows e Mac, as impressoras não são encontradas sozinhas
Aí o Docker corre dentro de uma máquina virtual, que não vê os anúncios que as
impressoras enviam para a tua rede. O agente funciona igual, mas as impressoras
adiciona-las tu, como se explica mais abaixo.
:::

## Confirma que está online

Volta ao BolloPrint: em menos de um minuto, o agente passa a **Online**.

![O agente no estado Online](/blog/media/2026-09-08-impresoras-red-local-agente/04-agente-online.png)

Se não passar, é quase sempre por uma de três causas: o manifesto **colado só em
parte**, o computador **sem internet** ou uma **firewall** a bloquear a saída.

## As tuas impressoras aparecem sozinhas

A partir daí, o agente **procura impressoras na tua rede** por conta própria a
cada 15 minutos. As que encontra aparecem numa lista com a sua marca e o seu
modelo, e tu decides:

- **Adicionar**: registas a impressora e ela começa a reportar.
- **Ignorar**: não é tua ou não a queres aqui.

![As impressoras encontradas na rede, com os botões de adicionar e ignorar](/blog/media/2026-09-08-impresoras-red-local-agente/05-encontradas.png)

Se acabaste de ligar uma máquina e não queres esperar, carrega em **Procurar
agora**. Algumas marcas pedem uma **palavra-passe** ao adicionar a impressora;
vemos isso mais abaixo.

## Se alguma não aparecer, adiciona-a tu

É **normal** uma impressora não aparecer sozinha em dois casos:

- **Está noutra rede.** Os anúncios das impressoras não passam de uma rede para
  outra.
- **O agente corre em Windows ou Mac.** Aí o Docker corre numa máquina virtual.

Não perdes nada com isso: adiciona-la tu e funciona exatamente igual, com câmara e
com comandos, se essa máquina os tiver. Carrega em **Adicionar por IP** e indica o
tipo de impressora, o seu endereço na tua rede e, se a pedir, a sua palavra-passe.

![O formulário para adicionar uma impressora pelo seu IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-anadir-por-ip.png "62%")

:::info 💡 Reserva-lhe o IP no router
Se o router mudar o endereço de uma impressora, voltamos a encontrá-la sozinhos,
mas vai estar em baixo durante algum tempo. Reservar-lhe o endereço evita essa
falha. É uma configuração do router, não do BolloPrint.
:::

## O que cada marca te pede

É aqui que surgem mais dúvidas. Em resumo:

| Marca | O que tens de fazer na máquina | Câmara | Podes pausar e cancelar? |
|---|---|---|---|
| **Bambu Lab** | Ativar o **Modo LAN** no ecrã dela e usar o **código de acesso** que te mostra | Sim | Sim, se também ativares o **Modo programador** |
| **Prusa** (MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Usar a **palavra-passe** que a própria impressora mostra | Ainda não | Sim |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Normalmente nada: costuma ligar-se sem palavra-passe | Sim, se tiveres webcam no teu Klipper | Sim |
| **Elegoo de resina** (Mars, Saturn, Jupiter) | Nada, não pede palavra-passe | Nos modelos que a trazem | Sim |
| **Elegoo Centauri Carbon 2** | Só se lhe puseste um código no ecrã | Sim | Ainda não |
| **FlashForge** (Adventurer 5M, 5M Pro, AD5X, Creator 5) | Ativar **LAN Only** e usar o código do ecrã | Sim | Ainda não |

:::warning ⚠️ Bambu Lab: o código de acesso muda
Sempre que ativas ou desativas o Modo LAN, a Bambu **gera um código novo**. Se
uma Bambu que funcionava bem deixa de repente de ligar, em nove de cada dez vezes
é por isto: vê outra vez o código no ecrã dela e atualiza-o no BolloPrint.
:::

:::info 💡 Não encontras o teu modelo na tabela?
Consulta as [impressoras compatíveis](/help/impresoras-compatibles). Se tiver
**Klipper** lá dentro (qualquer máquina montada por ti ou modificada), é
compatível, mesmo que a marca não apareça em nenhuma lista.
:::

## O que ganhas com o agente local

Com o agente a funcionar, tens:

- **Quase todas as marcas**: Prusa, Elegoo, Klipper, QIDI, Sovol, FlashForge,
  Voron… A nuvem não o oferece, porque só existe para a Bambu Lab.
- **Câmara**: em direto enquanto tens a página aberta, uma foto quando quiseres e
  uma foto final guardada no histórico de cada impressão. Não é videovigilância:
  não se grava nada.
- **Comandos**: pausar, retomar e cancelar a partir do BolloPrint, sem ires até à
  máquina, nas que o permitem (vê a tabela acima). Na Bambu Lab, com a impressora
  em **Modo LAN** e **Modo programador**.
- **Resistência às falhas de internet**: se a tua ligação cair, o agente
  **continua a ler as impressoras e guarda o que se passa**. Quando a ligação
  volta, envia tudo, e não perdes essas horas de histórico.
- **Independência do fabricante** e de que a nuvem dele continue a funcionar.

O que nenhuma via permite é **enviar trabalhos para imprimir**: o ficheiro
continuas a enviá-lo a partir do teu fatiador.

## Perguntas frequentes

As dúvidas que mais nos chegam.

### Tenho de abrir portas no router?

Não. Nem portas, nem IP fixo, nem regras de firewall. Funciona atrás de um router
doméstico normal.

### É preciso um agente por impressora?

Não. **Um só leva a frota inteira.** Só faz sentido ter vários se tiveres dois
espaços ou duas redes separadas.

### O que acontece se desligar o computador ou sair uma versão nova?

Quando o voltares a ligar, o agente volta sozinho. Também se atualiza sozinho:
quando sai uma versão nova, descarrega-a e reinicia com ela. Só terás de fazer
alguma coisa se te avisarmos no ecrã.

:::info 💡 Precisas de ajuda?
Escreve-nos a partir da [página de contacto](/contact) ou abre um tópico no
[nosso Discord](/help/soporte-por-discord). Se nos disseres que impressoras tens,
dizemos-te exatamente o que fazer com cada uma.
:::

## Documentação relacionada

- [Ligar impressoras](/help/conectar-impresoras): as duas vias e qual te convém
- [O agente local](/help/el-agente-local): a referência completa
- [Instalar o agente](/help/desplegar-el-agente): o detalhe técnico, se precisares
- [Tipos de ligação](/help/tipos-de-conexion): o que cada família de impressora permite
- [Impressoras compatíveis](/help/impresoras-compatibles): procura aqui o teu modelo
