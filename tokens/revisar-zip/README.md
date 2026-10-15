# Design tokens — login y registro

Este repositorio define un sistema de tokens en tres capas para el formulario de autenticación.

## Capas

1. **Primitivos** (`styles/tokens/_primitives.css`): valores crudos de paleta, medidas, tipografía y efectos. No describen el propósito visual.
2. **Semánticos** (`styles/tokens/_semantic.css`): asignan intención a los primitivos: fondo, superficie, texto, borde y acción. El tema claro es el predeterminado; `[data-theme="dark"]` redefine únicamente esta capa.
3. **Componente** (`styles/tokens/_component.css`): tokens propios del login, como `--button-bg`, `--button-radius`, `--input-bg` y `--hero-bg`. Estos apuntan a tokens semánticos.

## Ejemplo de referencia

`--color-blue-500` (primitivo) → `--color-action` (semántico) → `--button-bg` (componente) → `background: var(--button-bg)` en `styles/styles.css`.

Para cambiar la marca, se modifica la paleta en `_primitives.css`. Para cambiar el tema, se cambian los alias semánticos en `_semantic.css`. Para ajustar solamente el login, se modifica `_component.css`.

## Temas

El tema claro se aplica por defecto. Para activar el modo oscuro en el documento, agregá el atributo `data-theme="dark"` al elemento `<html>` o a un contenedor antecesor de los elementos que usan tokens. Para volver al tema claro, usá `data-theme="light"` o quitá el atributo.

Ejemplo en la consola del navegador:

```js
document.documentElement.dataset.theme = "dark";
// volver al claro:
document.documentElement.dataset.theme = "light";
```

El CSS de `Auth.jsx` no contiene colores hexadecimales escritos a mano: consume tokens de componente. El reset existente se conserva y se importa antes de las capas de tokens.

## Fuentes y fundamento

- **Design Tokens Community Group. (2026).** *Design Tokens Format Module 2025.10*, introducción. La especificación presenta los tokens como decisiones de diseño expresadas de forma independiente de la plataforma para compartir un vocabulario entre equipos y herramientas.
- **Salesforce. (s. f.).** *Design Tokens*. Lightning Design System. Explica que los tokens con nombre reemplazan valores codificados directamente y ayudan a mantener un sistema consistente.
- **IBM. (2026).** *Color*. Carbon Design System. Describe los tokens globales como colores compartidos, agrupados por el elemento de interfaz al que se aplican.
- **Comeau, J. W. (2021; actualizado en 2026).** *A Modern CSS Reset*. Fundamenta la decisión de mantener y poseer el código base propio en lugar de depender de un paquete externo.
- **Tailwind Labs. (2026).** *Theme variables*. Tailwind CSS v4. Explica cómo las decisiones de diseño de bajo nivel pueden almacenarse como variables de tema y reutilizarse.

## Referencias

- https://www.designtokens.org/TR/2025.10/format/
- https://www.lightningdesignsystem.com/design-tokens/
- https://carbondesignsystem.com/elements/color/tokens/
- https://www.joshwcomeau.com/css/custom-css-reset/
- https://tailwindcss.com/docs/theme
- https://m3.material.io/foundations/design-tokens/overview

## Entrega

Antes de abrir el Pull Request, ejecutar la aplicación del curso y verificar el login/registro en claro y oscuro. Adjuntar capturas reales de ambos estados al PR. El modo oscuro puede probarse con `document.documentElement.dataset.theme = "dark"` en la consola.
