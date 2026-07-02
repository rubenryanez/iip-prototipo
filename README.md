# Investment Intelligence Platform (IIP) — Prototipo

Prototipo navegable de la plataforma de asesoría **conviction-first** para Fondos Dinámicos (LarrainVial Asset Management × Consorcio). Transforma la revista mensual PDF en una herramienta interactiva para ejecutivos comerciales.

> Métrica de éxito del producto: *¿puede un ejecutivo demostrar en menos de 2 minutos el costo de una mala decisión de inversión?*

## Contenido

| Archivo | Descripción |
|---|---|
| `index.html` | **Versión alternativa (v2-alt)** — Home bento, acordeón de perfiles, dock inferior, grillas de tarjetas con modales, Modo Reunión con simulador, compartir por WhatsApp/mail. Es la versión que se sirve en la raíz del sitio. |
| `v1.html` | **Base aprobada (v1)** — diseño premium navy con sidebar lateral y hero cards. Accesible en `/v1`. |
| `vercel.json` | Configuración estática de Vercel (clean URLs + headers de seguridad). |

Ambos prototipos son **single-file**: HTML + CSS + JS embebidos, sin build, sin dependencias (solo Google Fonts vía CDN). Los datos provienen de la revista *Fondos Dinámicos* de mayo 2026 (series A/P/F/APV/APV-AP, retornos 2018–2026) y la encuesta oficial de perfilamiento FVTV008.

## Características principales

- **Investment Profile Engine**: encuesta oficial de 7 preguntas con puntajes y tramos exactos, en modal premium con blur.
- **ProductContext multi-vehículo**: Fondos Mutuos (A/P), Seguros con Ahorro (F), APV (APV/APV-AP) — toda la plataforma se recalcula al cambiar contexto.
- **Acordeón de perfiles**: Conservador → Agresivo con identidad cromática propia.
- **Modo Reunión**: vista de presentación para clientes con gráfico, mejores/peores meses, tiempos de recuperación y simulador de escenarios con monto manual.
- **Compartir resumen**: WhatsApp, email y copiar al portapapeles con el contexto activo.
- Cálculos financieros validados contra los retornos mensuales reales de la revista.

## Ejecutar localmente

No requiere instalación. Abrir `index.html` en el navegador, o servir la carpeta:

```bash
npx serve .
# o
python3 -m http.server 8080
```

## Deploy en Vercel

### Opción A — Dashboard (recomendada)

1. Crear un repositorio en GitHub y subir estos archivos (ver comandos abajo).
2. Entrar a [vercel.com/new](https://vercel.com/new) e **Import** el repositorio.
3. Configuración del proyecto:
   - **Framework Preset**: `Other`
   - **Build Command**: *(vacío)*
   - **Output Directory**: *(vacío — raíz)*
4. **Deploy**. Vercel entrega un link `https://<proyecto>.vercel.app`.

Cada `git push` a `main` generará un deploy automático con su propio link de preview.

### Opción B — CLI

```bash
npm i -g vercel
vercel          # primer deploy (preview)
vercel --prod   # deploy a producción
```

## Subir a GitHub

```bash
git init
git add .
git commit -m "IIP prototype: v2-alt (index) + v1 base"
git branch -M main
git remote add origin https://github.com/<TU_USUARIO>/<TU_REPO>.git
git push -u origin main
```

## URLs resultantes

- `https://<proyecto>.vercel.app/` → versión alternativa (v2-alt)
- `https://<proyecto>.vercel.app/v1` → base aprobada (clean URLs activadas)

## Notas

- Prototipo de diseño/UX: los datos están embebidos (no hay backend). La arquitectura data-driven con `/data/*.json` corresponde a la fase de implementación.
- Rentabilidades pasadas no garantizan rentabilidades futuras. Los valores de las cuotas de los fondos mutuos son variables. LarrainVial Asset Management Administradora General de Fondos S.A.
