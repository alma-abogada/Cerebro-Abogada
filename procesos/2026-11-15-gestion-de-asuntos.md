# Plantilla de gestión de asuntos con recordatorios · 2026-11-15

- **Qué pidió Alma:** una plantilla de gestión de proyectos con recordatorios. Eligió Excel + Google Calendar, para asuntos de clientes.
- **Qué se hizo:** Excel con pestañas Cómo usarla, Resumen, Asuntos y Tareas y plazos. Semáforo automático (vencido / urgente ≤3 días / próximo ≤15 días / en tiempo / hecho), fecha de aviso, conteo de pendientes por asunto, listas desplegables. Probado en Excel: sin errores. Trae un asunto de ejemplo (A-001, "Caso A") con 3 tareas para borrar.
- **Recordatorios:** skill nueva `al-plazos-calendario`. Ella dice "pasa mis plazos al calendario" y Claude crea los eventos en su Google Calendar con aviso al celular, y marca "Sí" en la hoja.
- **Dónde quedó:** en blanco en `plantillas/gestion-de-asuntos.xlsx`; la de trabajo en `privado/asuntos/gestion-de-asuntos.xlsx` (no se sube a GitHub).
- **Ojo:** su Google Calendar está en zona UTC; los eventos se crean con `America/Tijuana`. Le convendría cambiar la zona de su calendario a Tijuana.
