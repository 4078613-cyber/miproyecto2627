
# Instalación y configuración local con ProperDocs

## 1. Configuración de Git

Verifiqué la configuración global de Git desde la terminal de VS Code:

```bash
git config --global --list
```

![Configuración de Git](img/image1.png)

## 2. Autenticación en GitHub CLI

Instalé GitHub CLI y comprobé el estado de la autenticación:

```bash
gh auth status
```

![Autenticación de GitHub CLI](img/image2.png)

## 3. Herd con PHP 8.4

Instalé Herd y seleccioné PHP 8.4 para el entorno local.

![Herd con PHP 8.4](img/image3.png)

## 4. Repositorio clonado

Cloné el repositorio `misitio` y comprobé la configuración del remoto:

```bash
git remote -v
```

![Repositorio misitio clonado](img/image4.png)

## 5. Sitio local servido con HTTPS

Enlacé la carpeta `misitio` con Herd y verifiqué que el sitio se sirviera mediante HTTPS.

![Sitio misitio servido con HTTPS](img/image5.png)

## Resumen de Read the Docs

El documento utiliza títulos, texto, bloques de código e imágenes en Markdown. Read the Docs proporciona el tema y la navegación para organizar la documentación. No se requieren plugins adicionales para este contenido.
```
