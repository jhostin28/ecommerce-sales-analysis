# Instrucciones para la IA

Lee este archivo antes de ayudarme con cualquier proyecto. El plan de proyectos está en [README.md](README.md).

## Quién soy

Jhostin Raposo Chala, estudiante de último año de Desarrollo de Software en ITLA (Santo Domingo, RD).
Busco mi primer empleo como desarrollador junior (backend, data analyst, QA o AI) en RD o remoto.
Escribo en español. Los README de los proyectos van en inglés.

## Objetivo de cada proyecto

No es terminar rápido. Es **entender cada decisión** y poder **defenderla en una entrevista técnica**.
Si no lo puedo explicar sin ayuda, no está terminado.

## Cómo trabajamos

- **No me escribas el código completo.** Explícame, dame la estructura con espacios en blanco y yo lo completo.
- **Orden:** problema en palabras simples → modelo de datos → endpoints o pasos → código → Docker/CI al final.
- **Dinámica para código nuevo:** me pones un escenario cotidiano, yo explico en español qué debería pasar, me corriges y después vemos el código.
- **Si no entiendo algo:** dame otro ejemplo para que lo deduzca yo, y después dime qué significa.
- **Nombra cada parte del código** con su término (clase, objeto, método, función, propiedad, etc.).
- **En CRUD:** indica qué letra estamos construyendo (C, R, U o D).
- **Comandos:** explica qué hace cada comando y cada parte antes de que lo ejecute.
- **Comentarios en el código:** solo el "por qué". Las explicaciones largas van en el chat.
- **Respuestas cortas y directas.** Dime la realidad aunque no sea lo que quiero escuchar.

## Estructura de cada repo

```
README.md                         # En inglés: qué es, stack, tabla de fases con estado
docs/phase-N.md                   # Qué se hizo, decisiones y por qué, problemas reales
docs/troubleshooting/phase-N.md   # Tickets de troubleshooting de esa fase
AGENTS.md                         # Copia de estas instrucciones + contexto del proyecto
```

- **Fase 0 siempre:** definir el problema y las fases del proyecto. Las fases se deciden al empezar cada repo, no antes.
- **Una fase = una parte del sistema que funciona de principio a fin**, no un tema suelto.
- Cada fase termina con commit, su `docs/phase-N.md` y el estado actualizado en el README.

## Troubleshooting en cada fase

1. Un 🎫 ticket reportado por un "compañero" o "usuario" que diagnostico en mi propio proyecto.
2. Se rompe el código **a propósito** para ver el fallo en tiempo real.
3. El mismo problema como pregunta general de entrevista (no del proyecto).
4. Se documenta en `docs/troubleshooting/phase-N.md`.

## Anki

Mazo "Backend" con subdecks (API, Auth, CI, Data Modeling, Docker, JavaScript, SQL, Testing).
Tarjetas en inglés, como conocimiento general (no atado al proyecto), con tag `<proyecto>::phaseN`.

## Cambio de chat

- **Un chat por bloque, no por fase.** Una fase se divide en bloques pequeños (ej. fase 1: diseñar tablas → cargar CSV → limpieza → backup/usuario).
- **Al terminar un bloque:** guardar el resultado (commit o doc privado del proyecto de Claude), avisarme "⚠️ Buen momento para cambiar de chat" y darme el prompt para el siguiente.
- **Si el chat pasa de ~40 mensajes o se alarga a mitad de bloque:** avisarme antes de seguir, guardar dónde quedamos y darme el prompt para continuar.
- El contexto vive en el repo y los docs, no en el chat.

## Git

- Si estoy en la PC, yo hago los commits y el push (tú me das el código o texto).
- Solo haces push tú si estoy fuera de la PC o te lo pido. Después yo hago `git pull`.

## Al empezar un proyecto nuevo

1. Revisar en el [README.md](README.md) qué vacantes debe cubrir el proyecto.
2. Crear el repo con el nombre que dice el roadmap.
3. Copiar este archivo como `AGENTS.md` del nuevo repo y agregar el contexto del proyecto.
4. Hacer la fase 0: problema y fases.
5. Al terminar, actualizar el estado en este roadmap.

---

## Contexto de este proyecto: ecommerce-sales-analysis

- **Qué es:** análisis de ventas de un e-commerce con el dataset público de Olist (Brasil, 2016-2018, 9 CSV en Kaggle).
- **Vacantes que cubre:** Data Analyst Jr, BI Analyst, Analista Programador, Desarrollador de BD.
- **Stack:** SQL Server (T-SQL, vistas, procedimientos, funciones, triggers), SSMS, Excel avanzado (Power Query, tablas dinámicas, Power Pivot, conectado a SQL Server), Python (`pyodbc` + pandas: `read_sql`, `to_excel`), Power BI (relaciones y DAX).
- **Base del stack:** un analista de datos de un banco en RD dijo que usan Python, SQL avanzado, Excel avanzado, Power BI, SaaS corporativo y un software propietario. En el banco Python se usa para automatizar (ejecutar SQL y generar reportes) sin pandas. Decisión: conexión con `pyodbc` (lo del banco) + pandas encima (`read_sql` usa esa conexión), porque muchas vacantes piden pandas.
- **Ajustes por auditoría de vacantes reales de RD:** limpieza de datos, estadística descriptiva, KPIs comerciales, ventas contra meta, pronóstico simple, presentación ejecutiva, y lo mínimo de BD (backup, índice, usuario de solo lectura, función, trigger). **No se agregan más ajustes**; lo nuevo va a otro proyecto.
- **Privacidad:** el repo es público. Rechazos, CVs y vacantes van solo en los docs privados del proyecto de Claude, nunca aquí.
- **Por qué SQL Server:** bancos y gobierno en RD usan SQL Server + Power BI.
- **Un solo repo, una sola historia:** desarrollador de BD (tablas, vistas, procedimientos) → analista (Excel, Power BI, conclusiones) → jefe (decisión). Cada reclutador va a su carpeta: `sql/` para vacantes de BD; `excel/`, `powerbi/` y conclusiones para Data Analyst.
- **Diferencia con backend:** aquí se resuelve un problema de negocio. Flujo: **pregunta → dato → decisión**.
- **Excel avanzado:** Power Query, tablas dinámicas, BUSCARX, fórmulas anidadas (SI, SUMAR.SI.CONJUNTO, CONTAR.SI.CONJUNTO), formato condicional, gráficos. En entrevistas se prueba en vivo.
- **SQL avanzado:** las vistas usan CTE (`WITH`), subconsultas y funciones de ventana (`ROW_NUMBER`, `LAG`), no solo `SELECT` simples.

### Preguntas de negocio (fase 0)

1. ¿Estamos creciendo? Ventas mes a mes.
2. ¿Qué categorías dejan más dinero?
3. ¿Qué estados compran más?
4. ¿Cuántos pedidos llegan tarde y dónde?
5. ¿Las entregas tarde bajan las reseñas?

### Fases

🟢 = esencial para junior (lo piden casi todas las vacantes) · 🔵 = plus (diferencia o cubre vacantes de BD)

| Fase | Qué | Termina cuando |
|---|---|---|
| 0 | Problema y fases ✅ | Preguntas y plan en `docs/phase-0.md` |
| 1 | 🟢 Tablas con PK/FK, carga de los 9 CSV, **limpieza documentada** (nulos, categorías en portugués, duplicados) · 🔵 backup/restore, usuario de solo lectura | Los conteos cuadran, las FK no fallan y cada limpieza tiene su porqué |
| 2 | 🟢 Vistas con CTE y funciones de ventana, **estadística descriptiva** (media, mediana, comparar grupos), **KPIs comerciales** (ticket promedio, crecimiento mes a mes) · 🔵 pronóstico simple, 1 índice con plan de ejecución | Cada pregunta tiene su vista + respuesta en una frase |
| 3 | 🔵 Procedimientos con parámetros y `TRY/CATCH`, 1 función (`CREATE FUNCTION`), 1 trigger | Reporte por fechas o estado con `EXEC`; puedo explicar procedimiento vs. función vs. trigger |
| 4 | 🟢 Excel conectado a las vistas: Power Query, tablas dinámicas, BUSCARX, fórmulas, **ventas contra meta** (metas = supuesto documentado) · 🔵 Power Pivot | El gerente pulsa "Actualizar" y ve datos al día y el % de cumplimiento |
| 5 | 🔵 Python: conexión con `pyodbc` + pandas (`read_sql`, `to_excel`) que genera el reporte | Un solo comando produce el reporte |
| 6 | 🟢 Power BI conectado a las vistas: relaciones, DAX, KPIs, meta | El jefe ve las respuestas sin saber SQL |
| 7 | 🟢 Conclusiones en el README + **presentación ejecutiva** de 5 a 7 slides en PDF | Alguien ajeno entiende qué encontré y qué recomiendo |

**Orden de estudio si hay prisa:** 1, 2, 4, 6, 7 primero; 3 y 5 después.

### Estructura del repo

```
sql/        # 01-tables.sql, 02-views.sql, 03-procedures.sql
excel/      # report.xlsx
python/     # script de automatización del reporte
presentation/ # presentación ejecutiva (PDF)
powerbi/    # dashboard.pbix + capturas
docs/       # phase-N.md, troubleshooting/
data/       # CSV de Kaggle (ignorado por git)
```

### Notas

- Los CSV no se suben al repo. El README explica cómo descargarlos.
- Publicación del dashboard: Power BI "Publish to web" si la cuenta lo permite; si no, `.pbix` + capturas + PDF en el repo.
