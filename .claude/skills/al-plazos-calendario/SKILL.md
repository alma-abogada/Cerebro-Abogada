---
name: al-plazos-calendario
description: >-
  Lleva la hoja de gestión de asuntos de Alma (privado/asuntos/gestion-de-asuntos.xlsx) y pasa sus plazos, audiencias,
  entregas y cobros a su Google Calendar con aviso en el celular. Úsala SIEMPRE que diga "pasa mis plazos al calendario",
  "ponme los recordatorios", "¿qué tengo vencido / esta semana?", "agrega un asunto / una audiencia / un plazo",
  "¿cómo van mis asuntos?", aunque no diga "skill".
---

# Asuntos, plazos y recordatorios

**Archivo de trabajo:** `privado/asuntos/gestion-de-asuntos.xlsx` (con datos de clientes: nunca sale de `privado/`).
**Plantilla en blanco:** `plantillas/gestion-de-asuntos.xlsx` (sin datos; si se pierde el de trabajo, se copia de aquí).

Pestañas: `Cómo usarla`, `Resumen`, `Asuntos` (una fila por asunto, clave A-001…), `Tareas y plazos` (todo lo que tiene
fecha). Datos desde la fila 6. Columnas grises = fórmulas: no se escriben.

`Tareas y plazos`: A Clave · B Asunto (fórmula) · C Qué hay que hacer · D Tipo · E Fecha límite · F Hora ·
G Avisar días antes (vacío = 3) · H Fecha del aviso (fórmula) · I Estado · J Días que faltan · K Semáforo ·
L ¿En calendario? · M Notas.

## Antes de leer
Recuérdale en una línea que lo que lees se procesa en los servidores de Anthropic (regla 3), la primera vez en la sesión.

## "Pasa mis plazos al calendario"
1. Lee `Tareas y plazos` (pandas/openpyxl). Toma las filas con fecha en E, Estado distinto de "Hecho" y L vacío o "No".
   Omite las filas de ejemplo (Notas = "Ejemplo…") y avísale si siguen ahí.
2. Enséñale la lista (fecha, hora, qué, aviso) y espera su "sí" antes de crear nada.
3. Crea cada evento en su Google Calendar (`acastillo.integra@gmail.com`, conector de Google Calendar):
   - **timeZone `America/Tijuana` siempre**: su calendario está en UTC y sin esto la hora sale corrida.
   - Título: `[Tipo] Qué hay que hacer · Clave` (ej. `[Audiencia] Junta de herederos · A-001`). Sin nombre completo del
     cliente en el título; en la descripción puede ir la columna B y las notas.
   - Con hora (F): evento de 1 hora. Sin hora: evento de todo el día.
   - Avisos (`overrideReminders`, popup), con G = días antes (vacío = 3):
     - Con hora: `G × 1440` minutos y otro de 60 minutos.
     - Todo el día (empieza a medianoche): `G × 1440 − 480` (G días antes a las 8:00 am) y `960` (el día anterior a las
       8:00 am). Si G = 1, solo el de 960.
   - Sin invitados, `notificationLevel: NONE`.
4. Pon "Sí" en L de cada fila creada (openpyxl, sin `data_only`, para no borrar fórmulas) y guarda.
5. Si cambió una fecha (L en "No" y ya existía evento): búscalo por título en el calendario y actualízalo en vez de duplicar.

## "¿Qué tengo vencido / esta semana?"
Lee la hoja y responde en corto: VENCIDOS primero, luego URGENTES y PRÓXIMOS, con fecha y clave. No cambies nada.

## "Agrega un asunto / plazo"
Escribe la fila en la pestaña que toca (solo celdas blancas). Clave nueva = siguiente número libre. Pregunta lo que falte;
no inventes fechas ni plazos. Los plazos legales que ella dicte van tal cual; si te pide calcularlos, cita la fuente y
márcalo `[verificar]` (regla 4): la hoja cuenta días naturales, no hábiles.

## Al terminar
Nota corta en `procesos/` (sin nombres de clientes: claves o iniciales) y `al-guardar`.
