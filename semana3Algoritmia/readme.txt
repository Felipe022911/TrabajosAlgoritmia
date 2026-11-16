Taller de Lógica y Arquitectura de Componentes

Este documento contiene las pruebas de escritorio (trazas de ejecución) de los algoritmos **CajeroParqueadero** y **Piramide**, junto con el árbol de componentes de la página principal de la tienda de **Steam**[cite: 2].

---

1. Traza del Algoritmo: `CajeroParqueadero`

### Análisis del funcionamiento
El algoritmo utiliza un ciclo `Mientras` controlado por un valor centinela (`0`). Mientras el valor ingresado sea diferente de `0`, acumula el dinero cobrado en la variable `total` e incrementa en `1` el contador `carros`. Al ingresar `0`, finaliza el ciclo y muestra los totales.

### Prueba de escritorio (Simulación)
**Datos de entrada simulados:** `5000`, `12000`, `8500`, `0`

| Paso / Iteración | `valor` (Entrada) | Condición (`valor <> 0`) | `total` | `carros` | Salida en consola |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Inicio** | - | - | `0` | `0` | `"Valor cobrado (0 para cerrar caja):"` |
| **Lectura 1** | `5000` | `5000 <> 0` (**Verdadero**) | `5000` | `1` | `"Valor cobrado (0 para cerrar caja):"` |
| **Lectura 2** | `12000` | `12000 <> 0` (**Verdadero**) | `17000` | `2` | `"Valor cobrado (0 para cerrar caja):"` |
| **Lectura 3** | `8500` | `8500 <> 0` (**Verdadero**) | `25500` | `3` | `"Valor cobrado (0 para cerrar caja):"` |
| **Lectura 4** | `0` | `0 <> 0` (**Falso**) | `25500` | `3` | *Sale del ciclo `Mientras`* |
| **Fin** | - | - | `25500` | `3` | `"Carros atendidos: 3"`<br>`"Total recaudado: $25500"` |

---

## 2. Traza del Algoritmo: `Piramide`

### Análisis del funcionamiento
El algoritmo utiliza ciclos anidados para dibujar una pirámide centrada de altura `n`:
* **Ciclo externo (`fila`):** Controla cada nivel vertical desde `1` hasta `n`.
* **Primer ciclo interno (`j`):** Imprime `n - fila` espacios en blanco a la izquierda para centrar la figura.
* **Segundo ciclo interno (`j`):** Imprime `2 * fila - 1` asteriscos (`*`) correspondientes a ese nivel.

### Prueba de escritorio (Simulación)
**Dato de entrada simulado:** `n = 4`

| `fila` | Espacios (`n - fila`) | Asteriscos (`2 * fila - 1`) | Resultado impreso en la línea (`·` representa espacio) |
| :---: | :---: | :---: | :--- |
| **1** | `4 - 1 = 3` | `2(1) - 1 = 1` | `···*` |
| **2** | `4 - 2 = 2` | `2(2) - 1 = 3` | `··***` |
| **3** | `4 - 3 = 1` | `2(3) - 1 = 5` | `·*****` |
| **4** | `4 - 4 = 0` | `2(4) - 1 = 7` | `*******` |

**Salida visual final:**
```text
   *
  ***
 *****
*******

para la aplicacion elegi la de steam y esto es lo q se repite
SteamStorePage
├── GlobalHeader
│   ├── SteamLogo
│   ├── GlobalNavLinks (Tienda, Comunidad, Perfil, Soporte)
│   └── UserAccountBar
│       ├── InstallSteamButton
│       ├── NotificationBell
│       └── UserWalletBadge
│
├── StoreSubNav
│   ├── NavDropdown [🔄 Se repite] (Tu tienda, Nuevo y destacable, Categorías)
│   ├── WishlistCartButtons
│   └── StoreSearchInput
│
├── StoreBodyLayout
│   ├── LeftGutterSidebar (Columna lateral izquierda)
│   │   ├── SteamDeckBanner
│   │   └── SidebarLinkGroup [🔄 Se repite] (Recomendados, Explorar categorías, Explorar por género)
│   │       └── SidebarLink [🔄 Se repite]
│   │
│   └── MainStoreFeed (Columna central)
│       ├── FeaturedCarousel (Destacados y recomendados)
│       │   └── FeaturedGameSlide
│       │       ├── MainCapsuleImage
│       │       ├── ScreenshotThumbnailGrid
│       │       │   └── ScreenshotThumb [🔄 Se repite] (4 miniaturas)
│       │       ├── AvailabilityStatus
│       │       ├── DiscountBadge
│       │       └── PriceTag
│       │
│       ├── SpecialOffersSection (Ofertas especiales)
│       │   └── OfferCard [🔄 Se repite]
│       │       ├── CapsuleHeaderImage
│       │       ├── OfferTitle & Countdown
│       │       └── DiscountPriceBlock
│       │
│       ├── BrowseByCategoryCarousel (Explorar por categoría)
│       │   └── CategoryCard [🔄 Se repite] (Acción, RPG, Indie, etc.)
│       │
│       └── TabbedGameList (Novedades populares / Lo más vendido / Próximamente)
│           ├── TabSelector [🔄 Se repite]
│           ├── GameListColumn
│           │   └── GameRowItem [🔄 Se repite]
│           │       ├── SmallCapsuleImage
│           │       ├── GameTitle
│           │       ├── PlatformIcons [🔄 Se repite] (Windows, Mac, SteamOS)
│           │       ├── GenreTagList
│           │       └── DiscountPriceBlock
│           └── GamePreviewPanel (Panel derecho dinámico al hacer hover)
│               ├── PreviewTitle & ReviewSummary
│               ├── TagBadge [🔄 Se repite]
│               └── PreviewScreenshot [🔄 Se repite]
│
└── ValveFooter
    ├── ValveLogo
    ├── LegalText
    └── FooterLink [🔄 Se repite]
