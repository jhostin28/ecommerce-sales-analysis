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
- **Stack:** SQL Server (T-SQL, vistas, procedimientos almacenados), SSMS, Excel avanzado (Power Query, tablas dinámicas, conectado a SQL Server), Python (automatización con `pyodbc` + `openpyxl`, sin pandas), Power BI (relaciones y DAX).
- **Base del stack:** un analista de datos de un banco en RD dijo que usan Python, SQL (consultas avanzadas), Excel avanzado, Power BI, SaaS corporativo y un software propietario ("Aspec", no identificado). En el banco, Python se usa para automatizar: ejecutar SQL y generar reportes, no pandas.
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

| Fase | Qué | Termina cuando |
|---|---|---|
| 0 | Problema y fases | Preguntas y plan en `docs/phase-0.md` |
| 1 | Base de datos en SQL Server: tablas con PK/FK, carga de los 9 CSV, validación | Los conteos de filas cuadran con los CSV y las FK no fallan |
| 2 | Una vista T-SQL por pregunta (CTE, funciones de ventana) | Cada pregunta tiene su vista + respuesta en una frase |
| 3 | Procedimientos almacenados con parámetros y `TRY/CATCH` | Se puede pedir un reporte por rango de fechas o estado con `EXEC` |
| 4 | Reporte en Excel avanzado conectado a las vistas (Power Query, tablas dinámicas, fórmulas) | El gerente abre el Excel, pulsa "Actualizar" y ve datos al día |
| 5 | Automatización con Python: script que ejecuta un procedimiento y genera el reporte en Excel | Un solo comando produce el reporte sin abrir SSMS ni Excel |
| 6 | Dashboard en Power BI conectado a las vistas (relaciones, DAX) | El jefe ve las respuestas sin saber SQL |
| 7 | Conclusiones y recomendaciones en el README | Alguien ajeno entiende qué encontré y qué recomiendo |

### Estructura del repo

```
sql/        # 01-tables.sql, 02-views.sql, 03-procedures.sql
excel/      # report.xlsx
python/     # script de automatización del reporte
powerbi/    # dashboard.pbix + capturas
docs/       # phase-N.md, troubleshooting/
data/       # CSV de Kaggle (ignorado por git)
```

### Notas

- Los CSV no se suben al repo. El README explica cómo descargarlos.
- Publicación del dashboard: Power BI "Publish to web" si la cuenta lo permite; si no, `.pbix` + capturas + PDF en el repo.
