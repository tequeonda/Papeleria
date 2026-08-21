# Papelería · Onda Food — Instrucciones

## Qué hay en esta carpeta

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La app completa (los 3 modos) |
| `manifest.json` | Hace que se instale como app |
| `icon-192.png` | Ícono chico |
| `icon-512.png` | Ícono grande |

**Los 4 archivos van juntos.** Si falta el manifest o los íconos, no se instala bien como app.

---

## Paso 1 — Subir a GitHub

1. Entrá a github.com y creá un repositorio nuevo
2. Nombre sugerido: `papeleria` (dejalo **Público**)
3. Tocá "uploading an existing file"
4. Arrastrá **los 4 archivos** de esta carpeta
5. Tocá "Commit changes"

## Paso 2 — Activar GitHub Pages

1. En el repo, andá a **Settings** (arriba)
2. En el menú izquierdo, **Pages**
3. En "Source" elegí **Deploy from a branch**
4. Branch: **main**, carpeta: **/ (root)**
5. **Save**
6. Esperá 1-2 minutos

Tu link va a quedar así:

```
https://TUUSUARIO.github.io/papeleria/
```

## Paso 3 — Instalar como app

**Android (Chrome):**
Abrí el link → menú ⋮ → "Instalar app" o "Agregar a pantalla de inicio"

**iPhone (Safari):**
Abrí el link → botón compartir → "Agregar a pantalla de inicio"

**PC del local (Chrome):**
Abrí el link → ícono de instalar en la barra de direcciones (o ⋮ → Guardar y compartir → Crear acceso directo → tildar "Abrir como ventana")

**No pide login de ningún tipo.**

---

## Cómo funciona la sincronización

De fábrica viene en **modo WhatsApp**, que funciona sin configurar nada:

1. El local marca lo que falta y toca "Enviar reporte"
2. Se abre WhatsApp con el reporte armado y te lo manda
3. Vos abrís tu app → Compras → botón **📥** → pegás el mensaje
4. La app lo lee solo y arma la lista con precios

### Que te llegue directo a tu WhatsApp

Abrí `index.html` con cualquier editor de texto, buscá arriba de todo:

```javascript
var WA_COMPRAS   = "";
```

Y poné tu número con código de país, sin espacios ni signos:

```javascript
var WA_COMPRAS   = "5491122334455";
```

Guardá y volvé a subir el archivo a GitHub.

---

## Sincronización automática (opcional)

Si querés que el reporte le llegue solo a Compras sin pasar por WhatsApp:

1. Creá cuenta gratis en **jsonbin.io**
2. Creá un bin nuevo (contenido: `{}`)
3. Copiá el **Bin ID** y tu **Master Key**
4. En la app: Análisis → **⚙️ Config** → pegá los dos datos → Guardar
5. Repetí el paso 4 en el dispositivo del local

Desde ahí el local envía y a vos te aparece solo.

> ⚠️ La Master Key queda guardada en el navegador. Para stock de papelería está bien; no uses ese bin para nada sensible.

---

## El PIN

- **Local** entra sin PIN
- **Compras** y **Análisis** piden PIN

La primera vez que entres a Compras te pide crearlo. Anotalo — se guarda por dispositivo.

Si te lo olvidás: Análisis → Config → "Cambiar PIN". Si no podés entrar, borrá los datos del sitio desde el navegador y volvé a empezar.

---

## Editar los nombres de los productos

Los nombres que mandó el local no siempre coinciden con lo que pide el proveedor. Podés corregirlos:

**Análisis → 📝 Productos**

Ahí editás de cada producto:
- **Nombre** — como lo dice el local
- **Unidad** — texto libre: `caja`, `unid`, `bulto x50`, lo que necesites
- **Cantidad sugerida** — la que aparece precargada al armar el pedido
- **Producto de factura** — el vínculo que trae el precio. Si no lo vinculás, el producto no suma al costo estimado

También podés agregar productos nuevos o eliminar los que no uses.

### Pasar la lista corregida al local

Los cambios quedan en tu dispositivo. Para que el local vea los mismos nombres:

1. En tu app: Análisis → Productos → **📋 Copiar código del catálogo**
2. Mandáselo por WhatsApp al local
3. En la app del local: botón **📥 Actualizar lista** (arriba a la derecha) → pegar

Se hace una sola vez, o cada vez que cambies algo importante.

---

## Actualizar la app más adelante

Subí el `index.html` nuevo al repo reemplazando el viejo. Los datos guardados (facturas, armados, PIN) no se pierden porque viven en el navegador de cada dispositivo.
