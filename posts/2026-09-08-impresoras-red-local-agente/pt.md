---
slug: connect-printers-local-network-agent
title: "Liga as tuas impressoras pela tua própria rede: o agente local, passo a passo"
description: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge, Snapmaker, Klipper… Um agente pequeno num computador da oficina, toda a tua frota dentro do BolloPrint e sem mexer no router.
date: 2026-10-12
updated: 2026-10-16
tags: [tutoriais]
cover: 01-portada.webp
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
- **Atualiza-se sozinho**: quando sai uma versão nova, é ele que a instala.

::animation{id="local-agent"}

## Onde o instalar

O agente vive em **qualquer computador da oficina que não desligues**: um NAS, um
mini-PC, um Raspberry Pi ou o PC da oficina. Só precisa de estar **sempre ligado**
e de ter **Docker**.

O ideal é que esteja **na mesma rede que as impressoras**, porque assim
encontra-as sozinho. Se não for possível, adiciona-las à mão e funcionam igual.

## Cria o agente no BolloPrint

Começa no BolloPrint. Vai a **Configurações → Impressoras**. Vais ver três
separadores: **Impressoras** (todas as tuas máquinas, venham por onde vierem),
**Agente local** e **Bambu Cloud**. Abre **Agente local** e carrega em **Novo
agente**.

Dá-lhe um nome que ainda te diga alguma coisa daqui a seis meses: **dá-lhe o nome
do sítio onde está, não do que é**. «Rés do chão» ou «Pavilhão 2» servem;
«Agente 1», não. Depois carrega em **Criar agente**.

![O separador Agente local, com dois agentes online e o botão Novo agente](/blog/media/2026-09-08-impresoras-red-local-agente/02-nuevo-agente-pt.png)

## Copia o manifesto

Ao criá-lo, o BolloPrint mostra-te um **manifesto**: um texto que já traz
**escrito** tudo o que é teu, as chaves do teu agente e a versão certa. Não há
nada para substituir nem para preencher.

Escolhe o formato que usas (**Docker Compose** é o habitual), carrega em
**Copiar** e, quando o tiveres guardado num sítio seguro, em **Guardar**.

![O manifesto de instalação do novo agente, com o botão Copiar](/blog/media/2026-09-08-impresoras-red-local-agente/03-plantilla-pt.png "75%")

:::warning 🔐 Copia-o agora: as chaves só são mostradas uma vez
Não as guardamos, por isso não te podemos voltar a mostrá-las. Se perderes o
manifesto, não há problema: abre o agente com **Editar** (no menu **⋮** dele), vai
ao separador **Instalação** e carrega em **Regenerar chaves**. Se ainda nunca se
ligou, não se corta nada.
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

## Ficaste preso? Carrega em «Instalar»

Enquanto o agente não se tiver ligado pelo menos uma vez, a linha dele diz **Por
instalar**. Não é um erro: não caiu nada, só falta instalá-lo.

Nessa mesma linha tens o botão **Instalar**. Ao carregares nele, abrem-se os
passos que acabaste de ler, em resumo, com uma ligação para a **Ajuda**, outra
para este **Artigo do blog** e um botão para nos perguntares no **Discord**. Se
não guardaste o manifesto, o passo 3 leva-te diretamente a gerar um novo.

![Um agente por instalar com o painel Instalar aberto: os três passos, a ajuda e o Discord](/blog/media/2026-09-08-impresoras-red-local-agente/04-instalar-pt.png)

## Confirma que está online

Volta ao BolloPrint: em menos de um minuto, o agente passa a **Online**, com o
nome do computador onde corre e a versão que tem.

![O agente no estado Online](/blog/media/2026-09-08-impresoras-red-local-agente/05-en-linea-pt.png)

Se não passar, é quase sempre por uma de três causas: o manifesto **colado só em
parte**, o computador **sem internet** ou uma **firewall** a bloquear a saída. Se
quiseres ver o que o próprio agente reporta, abre-o com **Editar**: o separador
**Estado** dá-te os detalhes.

## As tuas impressoras aparecem sozinhas

A partir daí, o agente **procura impressoras na tua rede** por conta própria a
cada 15 minutos. Quando encontra alguma, avisa-te por cima dos separadores e
vê-la no fim de **Impressoras na rede local**, com a sua marca e o seu modelo. Tu
decides:

- **Adicionar**: registas a impressora e ela começa a reportar.
- **Ignorar**: não é tua ou não a queres aqui.

![Uma impressora detetada pelo agente, com os botões Ignorar e Adicionar, e por cima Procurar agora e Adicionar por IP](/blog/media/2026-09-08-impresoras-red-local-agente/06-encontradas-pt.png)

Se acabaste de ligar uma máquina e não queres esperar, carrega em **Procurar
agora**. Se uma impressora te vai pedir um código, a própria linha avisa-te antes
(«vai pedir o código de acesso»), para o teres à mão.

## Se alguma não aparecer, adiciona-a tu

É **normal** uma impressora não aparecer sozinha em dois casos:

- **Está noutra rede.** Os anúncios das impressoras não passam de uma rede para
  outra.
- **O agente corre em Windows ou Mac.** Aí o Docker corre numa máquina virtual.

Não perdes nada com isso: adiciona-la tu e funciona exatamente igual, com câmara e
com comandos, se essa máquina os tiver. Carrega em **Adicionar por IP**. São três
passos.

### 1. Escolhe a marca

Escolhe a marca da tua impressora: cada uma tem o seu cartão, e as que têm logótipo
aparecem primeiro. Não precisas de saber como a tua máquina comunica: disso
tratamos nós. Se escolheres **Elegoo**, perguntamos-te **Que Elegoo tens?**,
porque tem várias famílias. **Klipper** e **Outra de resina (ChituBox)** estão no
fim, em **Genéricas**, para uma máquina montada por ti ou uma marca que não está
na lista.

Se tens dúvidas se o teu modelo serve, em baixo tens **Não tens a certeza? Vê a
lista de compatíveis**; e se a tua impressora não estiver lá, diz-nos no Discord.

![O primeiro passo de Adicionar impressora por IP: as marcas que podes ligar](/blog/media/2026-09-08-impresoras-red-local-agente/08-anadir-marca-pt.png)

### 2. Escreve os dados dela

Só o indispensável:

- **Que agente a liga?**, se tiveres mais do que um. Só podes escolher um que
  esteja online.
- **IP da impressora**. Vê-a no ecrã da impressora (Definições → Rede) ou no teu
  router.
- **O código da impressora**, se essa marca o pedir. O campo chama-se como lhe
  chama o fabricante: numa Bambu, **Código de acesso LAN**.
- **Nome**, se lhe quiseres dar um teu. É opcional.

O **modelo e o número de série não os escreves**: é o agente que os pergunta à
impressora. Os campos obrigatórios têm um **asterisco vermelho** e ficam
contornados a vermelho enquanto estão vazios. No fim, o quadro **Lembra-te**
diz-te o que tens de preparar nessa marca antes de ligar.

![O segundo passo: o agente, o IP, o código de acesso LAN obrigatório e o quadro Lembra-te](/blog/media/2026-09-08-impresoras-red-local-agente/09-anadir-datos-pt.png)

### 3. Liga

Carrega em **Ligar** e vês como avança: o agente recebe o pedido, procura a
impressora nesse endereço e liga-se a ela. No fim, vais ver **«Ligada. Já está na
tua lista de impressoras.»**

![O terceiro passo: a impressora ligada e já na lista](/blog/media/2026-09-08-impresoras-red-local-agente/10-anadir-conexion-pt.png)

Se alguma coisa correr mal, dizemos-te **em palavras simples**: o que se está a
passar e o que verificar (nada responde nesse IP, a impressora recusa o
código…). Com **Voltar** corriges o dado e tentas outra vez. A mensagem original
da impressora fica recolhida em **Ver detalhe técnico**: se nos escreveres,
envia-nos esse texto e chegamos mais depressa à solução.

:::info 💡 Reserva-lhe o IP no router
Se o router mudar o endereço de uma impressora, voltamos a encontrá-la sozinhos,
mas vai estar em baixo durante algum tempo. Reservar-lhe o endereço evita essa
falha. É uma configuração do router, não do BolloPrint.
:::

## O que cada marca te pede

É aqui que surgem mais dúvidas. É o mesmo que te lembra o passo 2, em resumo:

| Marca | O que tens de fazer na máquina | Câmara | Podes pausar e cancelar? |
|---|---|---|---|
| **Bambu Lab** | Ativar o **Modo LAN** no ecrã dela (Definições → Rede) e usar o **código de acesso LAN** que te mostra | Sim | Sim, se também ativares o **Modo programador** |
| **Prusa** (beta: MK4, MK3.5, MK3.9, MINI, XL, CORE One) | Ativar o **PrusaLink** e usar a **palavra-passe** que mostra (não é a do Prusa Connect) | Ainda não | Sim |
| **Elegoo** (Saturn, Mars, Jupiter, Centauri Carbon) e **outras de resina (ChituBox)** | Nada, não pedem palavra-passe | Nos modelos que a trazem | Sim |
| **Elegoo Centauri Carbon 2** | Nada; só se lhe puseste um código no ecrã, escreve-o | Sim | Ainda não |
| **Anycubic** (beta: Kobra 3, Kobra S1, Kobra 4, Kobra X) | Ativar o **Modo LAN** (Definições → Rede). Com ele, a impressora deixa de usar a nuvem e a app da Anycubic | Ainda não | Ainda não |
| **FlashForge** (beta: Adventurer 5M, 5M Pro, AD5X, Creator 5) | Ativar o **LAN Only** e usar o código de verificação do menu de rede | Sim | Ainda não |
| **Snapmaker** (U1) | Nada | Sim | Sim |
| **Klipper** (QIDI, Sovol, Voron, RatRig, Creality K1…) | Normalmente nada: só se puseste uma chave de API no Moonraker | Sim, se tiveres webcam no teu Klipper | Sim |

:::warning ⚠️ Bambu Lab: o código de acesso muda
Sempre que ativas ou desativas o Modo LAN ou o Modo programador, a Bambu **gera um
código novo**. Se uma Bambu que funcionava bem deixa de repente de ligar, em nove
de cada dez vezes é por isto: vê outra vez o código no ecrã dela e atualiza-o no
BolloPrint. E tem em conta que o **Modo programador** a desliga da Bambu Cloud: a
partir daí só a vês através do agente.
:::

:::info 💡 Não encontras o teu modelo na tabela?
Consulta as [impressoras compatíveis](/help/impresoras-compatibles). Se tiver
**Klipper** lá dentro (qualquer máquina montada por ti ou modificada), é
compatível, mesmo que a marca não apareça em nenhuma lista.
:::

## O que ganhas com o agente local

Com o agente a funcionar, tens:

- **Quase todas as marcas**: Bambu Lab, Prusa, Elegoo, Anycubic, FlashForge,
  Snapmaker e tudo o que tem Klipper. A nuvem não o oferece, porque só existe para
  a Bambu Lab.
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
espaços ou duas redes separadas. Nesse caso, ao **Adicionar por IP** pergunta-te
qual a liga.

### O que acontece se desligar o computador ou sair uma versão nova?

Quando o voltares a ligar, o agente volta sozinho. Também se atualiza sozinho:
quando sai uma versão nova, descarrega-a e reinicia com ela, sem teres de mexer no
manifesto. Só terás de fazer alguma coisa se te avisarmos no ecrã.

### Porque é que não consigo carregar em «Adicionar por IP»?

Porque nenhum dos teus agentes está ligado, e o texto por baixo do botão diz-to.
Se ainda não o instalaste, usa **Instalar** na linha dele; se já funcionava,
confirma que o computador está ligado e com internet.

:::info 💡 Precisas de ajuda?
Escreve-nos a partir da [página de contacto](/contact) ou abre um tópico no
[nosso Discord](/help/soporte-por-discord). Se nos disseres que impressoras tens,
dizemos-te exatamente o que fazer com cada uma.
:::

Bom trabalho com toda a tua frota à vista, estejas onde estiveres.

![O Bollo, a mascote do BolloPrint, com óculos de oficina, em frente a uma quinta de impressoras 3D a trabalhar](/blog/media/2026-09-08-impresoras-red-local-agente/07-bollo.webp "60%")

## Documentação relacionada

- [Ligar impressoras](/help/conectar-impresoras): as duas vias e qual te convém
- [O agente local](/help/el-agente-local): a referência completa
- [Instalar o agente](/help/desplegar-el-agente): o detalhe técnico, se precisares
- [Tipos de ligação](/help/tipos-de-conexion): o que cada família de impressora permite
- [Impressoras compatíveis](/help/impresoras-compatibles): procura aqui o teu modelo
