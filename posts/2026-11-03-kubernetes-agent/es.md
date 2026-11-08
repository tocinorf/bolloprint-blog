---
slug: install-bolloprint-agent-kubernetes
title: "Pon en marcha el agente de BolloPrint en Kubernetes"
description: ¿Ya tienes k3s u otro clúster de Kubernetes en el taller? El agente es un Secret y un Deployment de una sola réplica. Créalo en BolloPrint, aplica el manifiesto y tus impresoras aparecen.
date: 2026-11-03
updated: 2026-11-03
tags: [tutoriales]
draft: true
---

Algunos talleres ya tienen un pequeño clúster de **Kubernetes**: k3s en un par de
mini-PCs, MicroK8s en un servidor, un homelab que fue creciendo. Si es tu caso, el
**agente local** encaja sin más: un Secret con sus claves y un Deployment con una
sola réplica.

- **Nada que editar**: BolloPrint te da el manifiesto con las claves ya dentro.
- **Sin Service, sin Ingress, sin puertos abiertos**: el agente llama a
  BolloPrint, nunca al revés.
- **Se actualiza solo**, sin que tengas que cambiar el manifiesto.

:::info 💡 ¿Todavía no usas Kubernetes?
No lo montes solo para el agente. [Docker](/blog/install-bolloprint-agent-docker),
o el paquete propio de tu equipo, te da exactamente lo mismo con menos piezas.
Tienes todas las opciones en [el agente local](/help/el-agente-local).
:::

## Qué necesitas

- Un clúster y `kubectl` con acceso a él.
- Un nodo **en la misma red que las impresoras**. El agente usa la red del nodo
  (`hostNetwork`) para encontrarlas, así que un pod que caiga en un nodo de otra
  red sigue funcionando, pero añadirás las impresoras por IP. Si tus nodos están
  en redes distintas, fija el Deployment al bueno con un `nodeSelector`.
- Para el volumen persistente (más abajo), una **StorageClass por defecto**.

Es ligero: el manifiesto le reserva 256 MB de memoria y no le deja pasar de
512 MB. La imagen funciona en nodos Intel/AMD y ARM, Raspberry Pi incluidas.

## 1. Crea el agente en BolloPrint

Ve a **Configuración → Impresoras**, abre la pestaña **Agente local** y pulsa
**Nuevo agente**. Elige **Kubernetes**, en **Con un contenedor**, ponle un nombre
(dónde está, no qué es) y pulsa **Crear agente**.

![La ventana Nuevo agente local, con Kubernetes en Con un contenedor](/blog/media/2026-11-03-kubernetes-agent/01-new-agent.png "75%")

## 2. Copia el manifiesto

Cambia a la pestaña **Kubernetes**. Te sale un **Secret** llamado
`bolloprint-agent` con las dos claves del agente, y un **Deployment** con el mismo
nombre, de una sola réplica, con la estrategia `Recreate` (nunca dos pods a la
vez), sin privilegios y con la red del nodo.

![El manifiesto de Kubernetes con Con volumen persistente marcado, el Secret con sus claves (aquí difuminadas) y el principio del Deployment](/blog/media/2026-11-03-kubernetes-agent/02-manifest.png "75%")

**Con volumen persistente** añade un PersistentVolumeClaim pequeño. Márcalo si tu
clúster tiene una StorageClass por defecto: el agente guarda ahí las versiones que
descarga, así que un reinicio del pod no lo devuelve unos minutos a la versión de
la imagen. Déjalo sin marcar si no hay StorageClass por defecto, o el pod se queda
esperando un volumen que no llega nunca y no arranca.

Pulsa **Copiar**, guarda el manifiesto en un lugar seguro y pulsa **Guardar**.

:::warning 🔐 Las claves se muestran una sola vez
No las guardamos. Si pierdes el manifiesto, abre el agente con **Editar**, ve a
**Despliegue** y pulsa **Regenerar claves**.
:::

## 3. Aplícalo

Guárdalo como `bolloprint-agent.yaml` y aplícalo:

```
kubectl apply -f bolloprint-agent.yaml
```

El manifiesto no lleva namespace, así que se crea en el que tengas activo. Si lo
prefieres aparte:

```
kubectl create namespace bolloprint
kubectl apply -n bolloprint -f bolloprint-agent.yaml
```

## 4. Comprueba que está en línea

En menos de un minuto, el agente pasa de **Sin instalar** a **En línea** en la
pestaña **Agente local**. Si no:

```
kubectl get pods -l app=bolloprint-agent
kubectl logs deployment/bolloprint-agent --tail 50
```

<!-- SCREENSHOT: 03-kubectl.png — a terminal (dark) showing `kubectl apply -f bolloprint-agent.yaml` creating secret/deployment(/persistentvolumeclaim) and `kubectl get pods -l app=bolloprint-agent` with the pod Running. Needs a real cluster (k3s is enough). -->
<!-- PENDING (uncomment when the screenshot exists): ![kubectl aplicando el manifiesto y el pod del agente en Running](/blog/media/2026-11-03-kubernetes-agent/03-kubectl.png) -->

Un pod que se queda en **Pending** es casi siempre el volumen persistente sin
StorageClass por defecto. Copia el manifiesto otra vez sin la casilla marcada, o
crea la StorageClass.

<!-- SCREENSHOT: 04-online.png — BolloPrint (English UI, dark theme), Settings → Printers → Local agent: an agent with the Kubernetes logo Online, with the node's name and its version. Needs that real cluster connected to the dev workshop. -->
<!-- PENDING (uncomment when the screenshot exists): ![El agente de Kubernetes En línea en BolloPrint](/blog/media/2026-11-03-kubernetes-agent/04-online.png) -->

A partir de aquí, tus impresoras aparecen solas, listas para **Añadir**: el resto
lo tienes en
[conecta tus impresoras por tu propia red](/blog/connect-printers-local-network-agent).

## Actualizaciones

El agente **se actualiza solo** desde la versión **2026.1.1**, nunca mientras
alguna de sus impresoras está imprimiendo. Si alguna vez BolloPrint te pide
actualizar a mano, cambia solo la versión de la línea `image:` y vuelve a
aplicar, o de una vez:

```
kubectl set image deployment/bolloprint-agent agent=ghcr.io/bolloprint/bolloprint-agent:<version>
```

(Si lo haces así, cambia también tu fichero, o el próximo `apply` te devuelve a la
versión antigua.) La versión que toca es la de la pestaña **Despliegue** del
agente.

:::warning ⚠️ No apliques el manifiesto de la pestaña Despliegue encima del tuyo
En un agente que ya existe lleva **CHANGE_ME** en lugar de las claves, y tu Secret
se quedaría con eso. Cambia solo la versión de la imagen.
:::

## Conviene saber

- **No subas las réplicas.** Un agente es un pod. Dos réplicas son dos agentes con
  las mismas claves peleándose por una sola conexión. Para repartir una flota
  grande, crea un segundo agente en BolloPrint.
- **Después de regenerar las claves, reinicia el pod.** Al aplicar el manifiesto
  nuevo cambia el Secret, pero el pod que ya corre no lo vuelve a leer solo:
  `kubectl rollout restart deployment/bolloprint-agent`.
- **Moverlo dentro del clúster no exige nada**: la identidad va en el Secret, así
  que un pod que cambia de nodo es el mismo agente. Para llevarlo a otro clúster,
  borra primero el Deployment en el antiguo y luego aplica el mismo fichero en el
  nuevo.
- **Para quitarlo**, elimínalo en BolloPrint (**⋮ → Eliminar**) y ejecuta
  `kubectl delete -f bolloprint-agent.yaml`.
- **Helm o Argo CD** valen, siempre que lo que llegue al clúster sea lo mismo: un
  Secret con las dos claves y un Deployment de una réplica. Guarda las claves
  donde guardes tus otros secretos, nunca en un repositorio público.

:::info 💡 ¿Necesitas ayuda?
Escríbenos desde la [página de contacto](/contact) o en
[nuestro Discord](/help/soporte-por-discord), con las últimas líneas de
`kubectl logs deployment/bolloprint-agent`.
:::

## Documentación relacionada

- [Agente en Kubernetes](/help/agente-en-kubernetes): todos los pasos y todos los detalles
- [El agente local](/help/el-agente-local): qué instalación te conviene
- [Impresoras por red local](/help/impresoras-por-red-local): añadir tus impresoras
