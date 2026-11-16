---
name: al-contrato-servicios
description: >-
  Prepara un contrato de prestación de servicios profesionales (iguala mensual) de Integra Legal para un cliente nuevo,
  en Word, a partir de su plantilla. Úsala SIEMPRE que Alma diga "hazme un contrato de prestación de servicios",
  "contrato de servicios profesionales para…", "contrato de iguala", "tengo un cliente nuevo, hazle su contrato",
  aunque no diga "skill". No es para arrendamientos ni compraventas.
---

# Contrato de prestación de servicios profesionales

Plantilla: `plantillas/contrato-prestacion-servicios.docx`. Formato y revisión: `conocimiento/formatos/contrato-prestacion-servicios.md`.

## 1. Datos que necesitas (pregúntalos en un solo mensaje)
- **Cliente**: ¿es persona moral o persona física? Necesitas:
  - razón social o nombre;
  - representante y su cargo;
  - datos del acta constitutiva: instrumento, volumen, notaría, notario y fecha;
  - RFC, actividad principal y domicilio.
- ¿Tiene **filiales** que también se van a atender? Si sí, nombre y acta de cada una.
- **Trámites** que se contratan: parte de la lista de la plantilla y pregunta qué se quita o se agrega.
- **Honorarios**: monto mensual, día de pago y forma de pago (efectivo o transferencia).
- **Poderes**: si se otorgan, con qué extensión territorial y por cuánto tiempo.
- **Duración** y fecha de firma.
- ¿Firman las dos profesionistas (Alma y la Lic. Rosa Angélica Valencia López) o solo Alma?
- Para la cláusula XVI: ¿los honorarios pendientes se cobran según el arancel o por la parte proporcional de la iguala?
- ¿Hay datos de los **testigos**?

Si ella pega o deja el acta o la constancia del cliente, antes de leerla recuérdale en una línea que lo que tú lees
se procesa en los servidores de Anthropic (regla 3).

## 2. Pasos
1. Copia la plantilla a `privado/clientes/<AAAA-MM-DD>-<iniciales>/contrato-prestacion-servicios.docx`. Lleva datos del
   cliente, así que **nunca** va en `entregables/`.
2. Llena el contrato con python-docx (`py` en Windows):
   - cambia cada campo **[EN CORCHETES]**;
   - quítale el resaltado;
   - borra las notas en cursiva que empiezan con "NOTA" o "Si el cliente…";
   - borra las partes opcionales que no se usen. Si se quitan declaraciones o cláusulas, **renumera** y revisa las
     referencias cruzadas: la cláusula VII remite a la declaración del domicilio del despacho, y la IX a la de las filiales.
3. Las cifras van con número y letra: "$12,000.00 m.n. (doce mil pesos moneda nacional)". Las fechas del proemio y del
   cierre van en letra.
4. Escribe las razones sociales igual en todo el contrato. En el contrato de octubre de 2026 cambiaban entre la
   Declaración Segunda y la Cláusula IX.
5. Revisa que no quede ningún "[" ni ningún resaltado, y que la numeración sea seguida.
6. Si ella lo pide, sácale un PDF con Word para revisarlo.

## 3. Qué revisa ella antes de firmar
- Las cláusulas XVII a XIX y el cambio a Centro de Conciliación los aprobó el 2026-11-15: ya no se le preguntan.
- La lista de trámites y el monto.
- Tú no decides cláusulas nuevas: las propones y ella decide (regla 4).

## 4. Guarda
Nota en `procesos/` solo con las iniciales del cliente o como "caso X", sin montos ni datos que lo identifiquen.
Después, commit y push con `al-guardar`. `privado/` no se sube a GitHub.
