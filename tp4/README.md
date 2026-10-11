# Coffea — Landing Page Estática (TP4)

Landing page estática de una sola página para la cafetería ficticia **Coffea**, replicando con fidelidad visual el diseño del template de Figma y siguiendo los requerimientos del documento `TP4 PRD_Landing_Coffea.pdf` (Secciones 1 a 9).

---

## 🛠 Stack Técnico y Restricciones
- **HTML5 semántico**: Un único `index.html` con landmarks estándar (`header`, `nav`, `main`, `section`, `article`, `figure`, `blockquote`, `figcaption`, `footer`), un único `<h1>` y jerarquía ordenada de `<h2>` y `<h3>`.
- **CSS3 Puro**: Organizado por capas `@layer tokens, base, layout, components, utilities;`.
- **Cero JavaScript**: Carruseles con `scroll-snap`, menú móvil con `<details>/<summary>`, botón de favoritos con `:checked`, validación de formulario nativa.
- **Sin preprocesadores ni frameworks**: 100% Vanilla CSS con CSS Custom Properties (Design Tokens), Flexbox y Grid.

---

## 📁 Estructura del Proyecto

```text
tp4/
├── index.html                 # Marcado semántico completo con landmarks y skip-link
├── css/
│   ├── main.css              # Declaración de @layer e imports en orden
│   ├── tokens.css            # Design tokens (colores, fuentes, escalas, radios, espacios)
│   ├── base.css              # Reset moderno, tipografía base, foco y accesibilidad
│   ├── layout.css            # Contenedor responsivo (.container) y franjas de fondo
│   ├── utilities.css         # Clases de utilidad (.visually-hidden, .text-truncate)
│   └── components/
│       ├── header.css        # Navegación flotante, logo y menú colapsable mobile
│       ├── hero.css          # Portada de 1000px, overlay de contraste, eyebrow y CTA
│       ├── categories.css    # Franja de 220px con 4 categorías e íconos temáticos
│       ├── product-card.css  # Tarjeta de producto con hover y favoritos sin JS
│       ├── carousel.css      # Riel con scroll-snap-type y flechas de navegación
│       ├── promo.css         # Banner de granos con imágenes laterales
│       ├── testimonial-card.css # Testimonios con card central destacada y paginador
│       ├── newsletter.css    # Formulario con validación nativa y granos de fondo
│       └── footer.css        # Pie de página de 6 columnas y enlaces a redes sociales
└── assets/
    ├── img/                  # Imágenes raster extraídas de Figma (hero, cafés, postres, etc.)
    └── icons/                # Íconos vectoriales SVG optimizados
```

---

## 🎨 Design Tokens Principales (`tokens.css`)

| Token | Valor | Uso |
| :--- | :--- | :--- |
| `--color-espresso` | `#30261C` | Texto principal, footer, botones primarios, títulos |
| `--color-maroon` | `#2A0000` | Botón "Order Now" de cards, precios, descripción |
| `--color-sand` | `#E2D9C8` | Franjas de categorías, promo, newsletter |
| `--color-sand-20` | `rgba(226, 217, 200, 0.2)` | Fondo de product-card |
| `--color-sand-40` | `rgba(226, 217, 200, 0.4)` | Fondo de testimonial-card |
| `--color-bg` | `#F1F0EE` | Fondo base de página, input del newsletter |
| `--color-muted` | `#544A3E` | Etiquetas de categorías |
| `--color-border-soft`| `rgba(48, 38, 28, 0.1)` | Borde de testimonios |
| `--color-text-soft` | `rgba(48, 38, 28, 0.7)` | Roles de testimonios |
| `--color-star` | `#FFB821` | Estrellas doradas de calificación |
| `--font-display` | `'Playfair Display', serif` | Logo, H1, títulos de sección, CTA, títulos footer |
| `--font-body` | `'Outfit', sans-serif` | Texto de hero, cards y botones |
| `--font-ui` | `'Poppins', sans-serif` | Enlaces, categorías, testimonios, newsletter |
| `--font-accent` | `'Reggae One', cursive` | Subencabezado "Come and Join" |

---

## 📱 Estrategia Responsive (Mobile-First)

- **Mobile (`360px - 767px`)**:
  - Contenedor con padding lateral de `16px`.
  - Menú hamburguesa accesible mediante `<details>/<summary>`.
  - Hero adaptativo (~640px de alto) con H1 escalado con `clamp()`.
  - Categorías en cuadrícula 2 × 2.
  - Carrusel con swipe nativo mostrando 1.2 cards para sugerir desplazamiento.
  - Imágenes laterales decorativas ocultas para optimizar lectura y carga.
  - Testimonios en carrusel de 1 card visible con snap centrado.
- **Tablet (`md: ≥ 768px`)**:
  - Contenedor con padding lateral de `32px`.
  - Categorías en una fila de 4 ítems.
  - Carrusel con 2.5 cards visibles.
  - Formulario de newsletter en línea con granos visibles.
  - Footer distribuido en 3 columnas.
- **Desktop (`lg/xl: ≥ 1024px / 1440px`)**:
  - Contenedor centrado a `1444px`.
  - Hero a `1000px` de altura exacta.
  - 4 cards completas visibles con flechas circulares de 71px.
  - Testimonios con card central destacada (`testimonial-card--featured`).
  - Footer en 6 columnas alineadas.

---

## ♿ Accesibilidad y Buenas Prácticas (WCAG 2.2 AA)
1. **Skip link** inicial hacia `#main` para lectores de pantalla.
2. **Textos alternativos (`alt`)**: Descriptivos para productos y avatares, y `alt=""` para imágenes puramente decorativas (granos, manos, fondos).
3. **Contraste visual**: Overlay gradiente en el Hero para garantizar ratio de contraste superior a 4.5:1 sobre imágenes oscuras.
4. **Navegación por teclado**: `:focus-visible` claramente delimitado con offset.
5. **Reducción de movimiento**: Consulta `@media (prefers-reduced-motion: reduce)` para anular transiciones y animaciones en usuarios sensibles.
6. **Dimensiones fijas**: Atributos `width` y `height` explícitos en todas las etiquetas `<img>` para prevenir saltos de diseño (Cumulative Layout Shift - CLS).
