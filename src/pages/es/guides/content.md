---
layout: ~/layouts/MainLayout.astro
title: Contenido de autoría
description: "Astro es una opción perfecta para tu proyecto centrado en el contenido: blogs, sitios de marketing, portafolios y más. Crea tu contenido directamente en tu proyecto, o conecta tu CMS de elección."
i18nReady: true
---
Astro es una opción perfecta para tu proyecto centrado en el contenido: blogs, sitios de marketing, portafolios y más.

Astro te ayuda a crear y presentar tu contenido. Puedes escribir una publicación de blog directamente en Astro usando Markdown/MDX, o buscar tu contenido desde un headless CMS. Astro te permite crear un sitio en torno a tu contenido: puedes agregar una plantilla a tus páginas, crear un índice de publicaciones y configurar un feed RSS para permitir que los lectores se suscriban.

## Escribir contenido

En Astro, puedes crear tu contenido de varias maneras: 
- En archivos Markdown (`.md` o [extensiones alternativas](/es/guides/markdown-content/)), diseñados para facilitar la escritura de contenido de texto enriquecido.
- En archivos MDX (`.mdx`), que te permiten incluir componentes y expresiones dinámicas en tu documento.
- Usando un sistema de administración de contenido (CMS) de terceros, luego extrayendo ese contenido a una página `.astro`.
- Otras opciones (menos utilizadas para páginas con mucho contenido) incluyen [Archivos `.astro`](/es/core-concepts/astro-pages/#páginas-de-astro) y [Archivos `.html`](/es/core-concepts/astro-pages/#páginas-html).

### Creación de Markdown

Markdown es una sintaxis conveniente para escribir texto enriquecido con formato básico y elementos comunes como encabezados, listas e imágenes. Astro tiene soporte incorporado para archivos Markdown en tu proyecto.

Crea y escribe un nuevo archivo `.md` en tu editor de código o trae un archivo existente escrito en tu editor Markdown favorito. Algunos editores de Markdown en línea como [StackEdit](https://stackedit.io/) y [Dillinger](https://dillinger.io) incluso te permitirán editar y sincronizar tu trabajo con tu repositorio de Astro almacenado en GitHub.

📚 Aprende más sobre [escribir contenido Markdown en Astro](/es/guides/markdown-content/).

### Autoría MDX

Si añades la integración MDX a tu proyecto, también puedes escribir una publicación usando archivos `.mdx`, que te permiten incluir expresiones JavaScript y componentes personalizados dentro de tu Markdown. Esto incluye tanto [componentes de Astro](/es/core-concepts/astro-components/) estáticos y [componentes del framework](/es/core-concepts/framework-components/) interactivos. Agrega elementos de la interfaz de usuario como un banner o un carrusel interactivo directamente en tu texto para convertir tu contenido en páginas web completas.

Escribe y edita archivos `.mdx` directamente en tu editor de código, junto con tus archivos del proyecto.

📚 Aprender más acerca de [utilizando MDX con Astro](/es/guides/integrations-guide/mdx/).

### Autoría de headless CMS

Escribe publicaciones de blog en tu sistema de administración de contenido (CMS) existente, como Storyblok, WordPress o Contentful. Algunos CMS, como Storyblok, proveen una [integración de Astro](https://www.storyblok.com/mp/announcing-storyblok-astro) oficial. Otros exponen un SDK de JavaScript que las páginas de Astro pueden usar para [obtener tu contenido remoto](/es/guides/data-fetching/#fetching-de-datos-desde-un-headless-cms).

## Administrar páginas de contenido

Los archivos Markdown y MDX que viven en tu directorio `src/pages` generarán automáticamente páginas en tu proyecto utilizando el [enrutamiento basado en archivos](/es/core-concepts/routing/) de Astro, creado en una URL correspondiente a la ruta del archivo de la publicación. 

También puedes optar por mantener tus archivos Markdown y MDX fuera del directorio `src/pages` y, en su lugar, [importar tu contenido](/es/guides/markdown-content/#importando-markdown) en páginas `.astro`.

Si estás escribiendo tu contenido en un CMS, puedes obtener tus publicaciones y usar el [enrutamiento dinámico](/es/core-concepts/routing/#rutas-dinámicas) para usar un archivo `.astro` para generar una ruta para cada publicación. En el modo estático predeterminado de Astro, estas rutas se generan en el momento de la compilación. Si optas por el [modo SSR](/es/guides/server-side-rendering/), respondes responde a una petición en tiempo de ejecución y obtienes el contenido a bajo petición.

## Mostrando tu contenido

Para crear funciones comunes para organizar y mostrar tu contenido, como un archivo de blog o una página para cada etiqueta de blog, Astro te permite [obtener nombres de archivo y metadatos](/es/reference/api-reference/#astroglob) desde tu Markdown y MDX frontmatter y utilizarlos para generar contenido de página y rutas.

## Integraciones de la comunidad

Además de la integración oficial [`@astrojs/mdx`](/es/guides/integrations-guide/mdx/), existen varias [integraciones comunitarias](https://astro.build/integrations/css+ui/?q=content) para trabajar con contenido en tu proyecto Astro.
