# Justificación Metodológica - Proyecto SmartBudget

# link https://muss3t.github.io/SmartBudget-Evaluacion-M3/
## Lección 1: El rol del Front-End en el proceso de diseño digital

El rol del desarrollador front-end es actuar como el puente vital entre la concepción visual de un producto (como un prototipo en Figma) y la interacción real del usuario. No se trata solo de "traducir" imágenes a código, sino de garantizar que la interfaz sea accesible, semánticamente correcta y escalable. 

En el caso de SmartBudget, una buena estructura HTML5 inicial asegura que la aplicación pueda crecer modularmente, permitiendo a los motores de búsqueda y tecnologías de asistencia interpretar correctamente la información antes de aplicar cualquier capa de estilo o comportamiento interactivo.

---

## Lección 2: Elección de Metodología CSS (BEM)

Para el desarrollo de la interfaz de SmartBudget se ha seleccionado la metodología **BEM (Block, Element, Modifier)** por las siguientes razones técnico-pedagógicas:

1. **Escalabilidad y Mantenimiento:** Al encapsular los estilos en bloques independientes (como `.hero` o `.card-feature`), podemos añadir nuevas secciones o modificar las existentes sin temor a generar efectos secundarios en cascada no deseados en el resto del sitio.
2. **Claridad en el HTML:** Al observar las clases en el HTML, cualquier desarrollador del equipo puede identificar inmediatamente la relación jerárquica. Por ejemplo, `navbar__link--active` expone claramente que pertenece al bloque `navbar`, afecta al elemento `link` y posee el modificador de estado `active`.
3. **Reducción de la Especificidad:** BEM promueve el uso de selectores de una sola clase en el CSS. Esto aplana la especificidad y evita las "guerras de selectores" donde se abusa del uso de ID o de la directiva `!important`.

## Lección 3: El Preprocesador SASS y la Arquitectura 7-1

Para mantener el código CSS limpio, escalable y libre de redundancias, se implementó el preprocesador **SASS** utilizando una adaptación de la arquitectura **7-1**. 

* **Abstracts:** Contiene variables globales (colores, tipografías) y mixins, lo que nos permite cambiar el tema visual de SmartBudget modificando un solo archivo.
* **Base:** Establece el reseteo del modelo de cajas (box-sizing) y estilos tipográficos base.
* **Layout / Components:** Divide los estilos por contexto (el encabezado general vs. los botones reutilizables), respetando la metodología BEM y aprovechando el *anidamiento* de SASS (`&__elemento`) para escribir código más ágil y estructurado.

## Lección 4: El Modelo de Cajas y Layout Responsivo

La disposición espacial de los elementos de SmartBudget se resolvió aplicando conceptos fundamentales del modelo de cajas (box-model) y sistemas de layout modernos:

* **Modelo de Cajas:** Se utilizaron propiedades como `padding` para el espacio interno de las secciones (respiración del diseño) y `margin: 0 auto` para el centrado de contenedores máximos, asegurando que el contenido no se estire infinitamente en pantallas ultra anchas.
* **Layout Responsivo:** En la sección de características (features), se implementó **CSS Grid**. Mediante el enfoque *Mobile First*, las tarjetas se apilan en una sola columna en dispositivos móviles y, mediante el uso de una *Media Query* (`min-width: 768px`), se distribuyen dinámicamente en tres columnas para pantallas de escritorio.

## Lección 5: Integración de Bootstrap 4

Para optimizar los tiempos de desarrollo y garantizar la consistencia transversal de la interfaz, se incorporó el framework **Bootstrap 4** mediante CDN.

* **Componentes implementados:** Se reemplazó la navegación estática por el componente `Navbar` (para dotarlo de un menú hamburguesa responsivo nativo). Las características se adaptaron al componente `Card` de Bootstrap para un acabado más prolijo, y se incorporó un `Modal` vinculado al botón principal para manejar la intención de registro del usuario.
* **Clases utilitarias:** Se aplicaron clases nativas como `py-5`, `mb-4`, `text-center`, `shadow-sm` y `text-primary` para manejar espaciados, tipografía y sombras directamente desde el HTML.
* **Integridad visual:** El archivo CSS/SASS personalizado (`main.css`) se cargó *después* de Bootstrap para mantener el control sobre componentes específicos (como la identidad de marca), asegurando una integración correcta sin sobreescrituras innecesarias.