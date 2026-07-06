# Protocolo NEMO

Este documento fija una convencion simple para trabajar con NEMO y con repositorios satelite como `hardware-lab`.

## Verbos de trabajo

- **Documenta**: crea o actualiza documentacion a partir del estado actual.
- **Consolida**: ordena notas dispersas, conversaciones o ideas en una estructura estable.
- **Registra**: anade una entrada cronologica de decision, experimento o descubrimiento.
- **Resume**: genera una version corta para transportar contexto a otro hilo.
- **Prepara**: redacta una receta, tarea o plan para ejecutar despues.
- **Aplica**: modifica archivos del repositorio.
- **Sube progreso**: documenta el punto actual y persiste los cambios en GitHub.
- **Publica**: crea rama, commit, push y PR cuando se quiera flujo de revision.

## Marcas semanticas

Para evitar mezclar hechos con intuiciones:

- `OBSERVADO`: comprobado en hardware, software o entorno real.
- `HIPOTESIS`: razonamiento plausible, pendiente de validacion.
- `DECISION`: criterio adoptado para avanzar.
- `PENDIENTE`: tarea o experimento por hacer.
- `RIESGO`: punto que puede bloquear, confundir o romper el diseno.

## Relacion entre repositorios

- `hardware-lab`: evidencia experimental, comandos, resultados, hardware concreto.
- `nemo`: memoria conceptual, arquitectura, decisiones transversales y continuidad entre proyectos.

Cuando un hallazgo tenga impacto en arquitectura general, debe quedar en ambos sitios:

```text
hardware-lab -> que se probo y que ocurrio
nemo         -> que significa para el diseno del sistema
```

## Formato recomendado de nota NEMO

```text
# Titulo

Fecha:
Origen:
Repos relacionados:

## Contexto
## Observaciones
## Interpretacion
## Decision o consecuencia
## Proximos pasos
```

## Convencion de ordenes cortas

- `Sube progreso a X`: actualizar documentacion del repo X con el estado actual.
- `Sube progreso a X y NEMO`: registrar evidencia en X y significado arquitectonico en NEMO.
- `Deja receta para Cursor`: generar un Markdown accionable orientado a implementacion.
- `Haz pergamino`: convertir una fase o idea grande en documento narrativo/estructurado.
