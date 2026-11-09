# Pulso · Formulario de suscripción con EmailJS

- `index.html` — landing con un solo campo (Email). Al enviarlo, EmailJS manda el correo de bienvenida.
- `email-template.html` — plantilla del correo: tablas + CSS inline, 5 secciones (Logo, Saludo, Contenido, Botón CTA, Footer) y un preheader.

## Configurar EmailJS (≈5 min)

1. Crea una cuenta en https://www.emailjs.com (plan gratis: 200 correos/mes).
2. **Email Services → Add New Service → Gmail** → conecta tu cuenta → copia el **Service ID**.
3. **Email Templates → Create New Template**:
   - **To Email:** `{{user_email}}`
   - **Subject:** `¡Bienvenido a Pulso! Tu suscripción está confirmada`
   - **From Name:** `Pulso`
   - En **Content → Edit Content → Code Editor**, pega todo el contenido de `email-template.html`.
   - Guarda y copia el **Template ID** (pestaña Settings).
4. **Account → General** → copia la **Public Key**.
5. En `index.html`, reemplaza `TU_PUBLIC_KEY`, `TU_SERVICE_ID` y `TU_TEMPLATE_ID`.

Variables que envía el formulario: `{{user_email}}`, `{{subscribe_date}}`, `{{site_url}}`.

## Publicar

Cualquier hosting estático sirve (GitHub Pages, Netlify Drop, Vercel). Con GitHub Pages:

```bash
git init && git add . && git commit -m "Formulario de suscripción con EmailJS"
gh repo create pulso-emailjs --public --source=. --push
gh api -X POST repos/{owner}/pulso-emailjs/pages -f "source[branch]=main" -f "source[path]=/"
```

El link queda en `https://<tu-usuario>.github.io/pulso-emailjs/`.
