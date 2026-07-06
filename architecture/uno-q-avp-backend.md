# UNO Q como backend grafico residente para AVP

Fecha: 2026-07-06
Origen: investigacion sobre Arduino UNO Q en modo SSH/headless
Repos relacionados: `hardware-lab`

## Contexto

Durante la exploracion del Arduino UNO Q surgio una duda critica: si el dispositivo arranca sin monitor conectado y se usa como nodo SSH, puede seguir existiendo una capa grafica util?

La respuesta observada es importante para la idea de un AVP, un procesador de video moderno desacoplado del hardware fisico de salida.

## Observaciones

`OBSERVADO`: el UNO Q arranca sin monitor conectado y aun asi alcanza `graphical.target`.

`OBSERVADO`: `LightDM` y `Xorg :0` estan activos en modo SSH/headless.

`OBSERVADO`: existen nodos DRM:

```text
/dev/dri/card0
/dev/dri/renderD128
```

`OBSERVADO`: desde SSH se puede hablar con X11 usando:

```bash
sudo XAUTHORITY=/var/run/lightdm/root/:0 DISPLAY=:0 xrandr --verbose
```

`OBSERVADO`: sin monitor, `DP-1` aparece como desconectado, pero X11 mantiene una pantalla logica de 1024x768.

`OBSERVADO`: al conectar monitor despues del arranque, `DP-1` pasa a `connected`, se lee EDID y aparecen modos reales.

`OBSERVADO`: la salida puede necesitar reactivacion manual:

```bash
sudo XAUTHORITY=/var/run/lightdm/root/:0 DISPLAY=:0 xrandr --output DP-1 --off
sleep 1
sudo XAUTHORITY=/var/run/lightdm/root/:0 DISPLAY=:0 xrandr --output DP-1 --auto
```

Resultado observado: aparece el escritorio del UNO Q.

## Interpretacion

El UNO Q no parece alternar entre dos personalidades totalmente separadas:

```text
SBC visual
nodo SSH sin graficos
```

El modelo mental mas util es:

```text
sesion grafica residente visible
sesion grafica residente invisible
```

Es decir, el sistema grafico puede estar vivo aunque no haya salida fisica activa.

## Consecuencia arquitectonica

`DECISION`: no conviene plantear el STM32 como generador principal de video.

Reparto conceptual preferido:

```text
STM32
  - entradas fisicas
  - GPIO
  - shields UNO R4
  - joysticks, sensores, buses lentos
  - posible pantalla auxiliar SPI/I2C

Qualcomm / Debian
  - backend grafico
  - X11/DRM/KMS
  - renderer principal
  - salida USB-C/DisplayPort
```

Para un AVP, el Qualcomm puede ser la primera implementacion de referencia del backend de presentacion.

## AVP como maquina virtual de video

La idea emergente no es replicar electricamente un VDP clasico, sino definir una interfaz estable:

```text
SetMode()
SetPalette()
WriteVRAM()
LoadTiles()
Sprite()
Scroll()
Blit()
Interrupt()
```

Debajo de esa interfaz puede haber distintos backends:

```text
UNO Q + X11/DRM
Raspberry Pi + DRM
PC + SDL/OpenGL
Navegador + WebGL/WebGPU
Pantalla SPI auxiliar
```

El software que hable con el AVP no deberia depender del backend fisico.

## Decision de diseno

`DECISION`: tratar el AVP como una maquina virtual de video con backend intercambiable.

El UNO Q se convierte en una plataforma candidata para validar:

- render residente sin monitor inicial;
- hotplug de salida fisica;
- aplicacion fullscreen retro;
- separacion entre motor grafico y dispositivo de salida;
- comunicacion futura con STM32 para entradas y eventos.

## Proximos pasos

`PENDIENTE`: definir un `Lab Mode` sin DPMS, salvapantallas ni suspension.

`PENDIENTE`: construir una app visual minima que pinte en `DISPLAY=:0`.

`PENDIENTE`: arrancar sin monitor, dejar la app corriendo, conectar monitor despues y comprobar si la app aparece ya en ejecucion.

`PENDIENTE`: definir un primer borrador de API AVP: modos, memoria virtual, comandos y eventos.
