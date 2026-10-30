# Enchastre.bba — Sitio autogestionable

Sitio web de la marca **Enchastre.bba** con panel de administración visual.

## ¿Qué cambió?

- El contenido (textos, colores, tipografías, productos e imágenes) ahora se guarda de forma **persistente**.
- Panel de administración profesional en `/admin`.
- Imágenes se suben a **Cloudinary** (rápidas y optimizadas).
- Los cambios se publican automáticamente a través de GitHub + Netlify.
- Se eliminó la contraseña insegura que estaba en el código.

---

## Estructura del proyecto

```
/
├── index.html              ← Página pública
├── admin/
│   ├── index.html          ← Panel de administración (Decap CMS)
│   └── config.yml          ← Configuración del panel
├── data/
│   ├── site.json           ← Textos, colores, tipografías, Instagram, imagen de marca
│   └── products.json       ← Los 12 productos del catálogo
├── netlify.toml            ← Configuración de Netlify
└── README.md
```

---

## Pasos para poner en marcha (hacer una sola vez)

### 1. Subir estos archivos a GitHub

1. Entrá a tu repositorio: https://github.com/camivicjuarez-design/enchastre
2. Subí **todos** los archivos y carpetas de este proyecto (reemplazando el `index.html` anterior).
3. Asegurate de que la rama sea `main`.

### 2. Activar Identity y Git Gateway en Netlify

1. Entrá a [app.netlify.com](https://app.netlify.com) → tu sitio **enchastresosvos**.
2. Andá a **Site configuration** → **Identity**.
3. Hacé clic en **Enable Identity**.
4. En **Registration preferences** elegí **Invite only** (solo vos podés entrar).
5. Más abajo, en **Services** → **Git Gateway** → **Enable Git Gateway**.
6. (Opcional pero recomendado) En **External providers** habilitá **GitHub**.

### 3. Crear cuenta gratuita en Cloudinary (para las imágenes)

1. Registrate en [https://cloudinary.com/users/register/free](https://cloudinary.com/users/register/free)
2. Una vez dentro, en el Dashboard vas a ver:
   - **Cloud name**
   - **API Key**
3. Copiá esos dos valores.

### 4. Configurar Cloudinary en el panel

Abrí el archivo `admin/config.yml` y reemplazá estas dos líneas:

```yaml
cloud_name: TU_CLOUD_NAME
api_key: TU_API_KEY
```

por tus valores reales de Cloudinary.

Hacé commit y push de ese cambio.

### 5. (Recomendado) Variables de entorno en Netlify

En Netlify → Site configuration → Environment variables, podés agregar:

- `CLOUDINARY_CLOUD_NAME`
- `CLOUDINARY_API_KEY`

(No es obligatorio si ya pusiste los valores en `config.yml`).

---

## Cómo usar el panel de administración

1. Andá a: **https://enchastresosvos.netlify.app/admin/**
2. Iniciá sesión con tu cuenta de GitHub (o el mail que configuraste en Identity).
3. Vas a ver dos secciones principales:
   - **Configuración general** → textos, colores, tipografías, Instagram e imagen de marca
   - **Productos** → los 12 modelos (nombre, precio, foto y texto alternativo)
4. Hacé los cambios que quieras.
5. Pulsá **Publish** / **Publicar**.
6. En 1–3 minutos Netlify actualiza el sitio y los visitantes ven los cambios.

---

## Flujo de trabajo diario

| Acción                        | Dónde                          | Resultado                          |
|-------------------------------|--------------------------------|------------------------------------|
| Cambiar un texto              | /admin → Configuración general | Se publica para todos              |
| Cambiar colores               | /admin → Colores               | Se aplica en todo el sitio         |
| Cambiar tipografía            | /admin → Tipografías           | Se actualiza títulos o cuerpo      |
| Subir / reemplazar foto       | /admin → Productos o Imagen de marca | Imagen optimizada en Cloudinary |
| Cambiar precio o nombre       | /admin → Productos             | Catálogo actualizado               |
| Cambiar Instagram             | /admin → Instagram             | Todos los botones apuntan al nuevo |

---

## Recuperar una versión anterior

Como todo se guarda en GitHub:

1. Andá al repositorio en GitHub.
2. Hacé clic en el archivo que querés recuperar (por ejemplo `data/site.json`).
3. Pulsá **History** → elegí el commit anterior → **Restore this file**.
4. Netlify volverá a desplegar automáticamente.

---

## Notas importantes

- La primera vez que entres a `/admin` puede pedirte que invites tu propio email desde Netlify Identity.
- Las imágenes se optimizan automáticamente (formato WebP, calidad automática).
- No borres los campos `id` de los productos.
- Si algo no carga, borrá la caché del navegador o esperá 2 minutos después de publicar.

---

## Soporte técnico

Si necesitás ayuda con algún paso de la configuración inicial (Identity, Cloudinary o el primer login), decime en qué punto estás y te guío.
