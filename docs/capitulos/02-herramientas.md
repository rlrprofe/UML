# 2. Herramientas CASE

## 2.1. Qué es una herramienta CASE

**CASE** son las siglas de *Computer-Aided Software Engineering*: ingeniería del software asistida por ordenador. Una **herramienta CASE** es cualquier programa que ayuda a realizar alguna tarea del desarrollo de software: analizar, diseñar, generar código, probar o documentar.

Las que dan soporte a UML permiten, según su nivel, cosas como estas:

| Capacidad | Qué aporta |
|---|---|
| **Dibujo** | Paleta de símbolos UML, conectores que se «pegan» a las cajas, plantillas |
| **Validación** | Avisa si el diagrama incumple las reglas de la notación |
| **Repositorio del modelo** | Guarda los elementos una sola vez y los reutiliza en varios diagramas: si renombras una clase, cambia en todos |
| **Generación de código** (ingeniería directa) | Crea el esqueleto del código a partir del diagrama |
| **Ingeniería inversa** | Crea el diagrama a partir del código existente |
| **Documentación y exportación** | Imágenes, PDF o webs a partir del modelo |
| **Trabajo en equipo** | Compartir y versionar modelos |

No todas las herramientas ofrecen todo: unas son simples **programas de dibujo** con símbolos UML, y otras son **herramientas CASE completas** con repositorio de modelo y sincronización con el código.

## 2.2. Cómo elegir una herramienta

No existe «la mejor»: depende de para qué la vayas a usar. Estos son los criterios más habituales:

- **Coste y licencia**: ¿es gratuita? ¿también para docentes y para uso profesional?
- **Plataforma**: ¿funciona en tu sistema operativo? ¿en el navegador?
- **Tipos de diagrama**: ¿incluye los que necesitas (clases, casos de uso, secuencia, actividades, estados)?
- **Generación de código e ingeniería inversa**: ¿para qué lenguajes?
- **Formato de archivo**: ¿es abierto y legible? ¿se puede guardar en **Git** y ver qué cambió entre versiones?
- **Curva de aprendizaje**: ¿cuánto tarda alguien en producir su primer diagrama?

## 2.3. Las herramientas del curso

En este curso trabajaremos con dos herramientas que se complementan, y veremos otras para generar código.

| | **draw.io** | **PlantUML en VS Code** |
|---|---|---|
| **Forma de trabajar** | Dibujas arrastrando símbolos | Escribes el diagrama como texto y se dibuja solo |
| **Coste** | Gratuita | Gratuita |
| **Dónde funciona** | Navegador y aplicación de escritorio | Dentro de Visual Studio Code |
| **Tipos de diagrama** | Todos, con bibliotecas de formas UML | Clases, casos de uso, secuencia, actividades, estados… |
| **Archivo** | `.drawio` (XML) | `.puml` (texto plano) |
| **Versionable en Git** | Posible, pero los cambios son poco legibles | Sí: se ve línea a línea qué cambió |
| **Colocación de las cajas** | Tú decides | Automática |
| **Genera código / ingeniería inversa** | No | No directamente (existen utilidades externas) |
| **Ideal para** | Aprender la notación, bocetos y diagramas con aspecto cuidado | Diagramas que viven junto al código y cambian a menudo |

!!! info "¿Son herramientas CASE?"
    Hablando con rigor, draw.io y PlantUML son herramientas de **diagramación**: dibujan UML, pero no mantienen un repositorio de modelo ni sincronizan con el código. Son perfectas para aprender y para el día a día. Las capacidades de generación de código e ingeniería inversa se estudian en el capítulo 10, donde se indica la herramienta con la que se practica.

## 2.4. draw.io

[draw.io](https://www.drawio.com/) (también llamado *diagrams.net*) es un editor de diagramas gratuito. Se usa **en el navegador**, sin instalar nada, o como **aplicación de escritorio**.

### Primeros pasos

1. Abre la aplicación y crea un diagrama en blanco (o abre uno existente con `.drawio`).
2. Activa las **formas UML**: en la parte inferior de la barra lateral izquierda pulsa **Más formas** (*More Shapes*) y marca **UML** (y, si quieres, **UML 2.5**).
3. También puedes partir de una **plantilla**: menú **Organizar → Insertar → Plantilla** y busca en las categorías *Software* y *UML*.

### Dibujar una clase

1. Arrastra al lienzo la forma **Class** de la biblioteca UML.
2. Haz doble clic en el nombre y escribe `Coche`.
3. En el compartimento de atributos escribe, una línea por atributo: `- matricula : String`, `- velocidad : int`.
4. En el compartimento de operaciones escribe `+ acelerar(incremento : int) : void` y `+ getVelocidad() : int`.
5. Guarda el diagrama con **Archivo → Guardar** (formato `.drawio`).

### Guardar y exportar

- El archivo `.drawio` es el **editable**: guárdalo siempre.
- Para insertar el diagrama en un documento, usa **Archivo → Exportar como** y elige **PNG**, **SVG** o **PDF**.

!!! tip "Consejos"
    - Usa los **conectores** de la barra (no líneas sueltas) para que las flechas sigan a las cajas cuando las muevas.
    - Si borras una clase, revisa que no queden flechas colgando.
    - Una carpeta por proyecto y un nombre por diagrama (`clases-alquiler.drawio`) te ahorrará muchos disgustos.

## 2.5. PlantUML en Visual Studio Code

**PlantUML** es un lenguaje que describe diagramas UML **con texto**. Tú escribes qué elementos hay y cómo se relacionan, y la herramienta decide cómo dibujarlos. La extensión de VS Code [PlantUML (jebbs)](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml) añade a VS Code la vista previa y la exportación.

### Instalación

1. Instala **Java**: el JDK del módulo te sirve. Compruébalo con `java -version` en una terminal.
2. En VS Code abre **Extensiones** (`Ctrl+Shift+X`), busca **PlantUML** del autor *jebbs* e instálala.
3. Según la ficha de la extensión, para dibujar en local necesita Java y **Graphviz**; en Windows incluye el `plantuml.jar` y Graphviz, y en otros sistemas hay que instalar Graphviz aparte.

!!! note "Si no puedes instalar Graphviz"
    La extensión permite cambiar en los ajustes el modo de dibujo a un **servidor PlantUML** (busca `plantuml render` en los ajustes). Así no necesitas instalar nada más, aunque el texto del diagrama se envía a ese servidor.

### Tu primer diagrama

1. Crea un archivo `coche.puml`.
2. Escribe este contenido:

```text
@startuml
skinparam classAttributeIconSize 0

class Coche {
  - matricula : String
  - velocidad : int
  + acelerar(incremento : int) : void
  + getVelocidad() : int
}
@enduml
```

3. Pulsa `Alt+D` para abrir la **vista previa**: verás la clase dibujada y se actualiza al escribir.
4. Para guardar la imagen, abre la **paleta de comandos** (`Ctrl+Shift+P`) y ejecuta **PlantUML: Export Current Diagram**.

Todo diagrama PlantUML va entre `@startuml` y `@enduml`. La línea `skinparam classAttributeIconSize 0` hace que la visibilidad se vea con los símbolos `+` y `-` en lugar de los iconos de colores.

### Una relación

Las relaciones se escriben con flechas hechas de caracteres. Por ejemplo, una flota que agrupa vehículos:

```text
@startuml
class Flota
class Vehiculo
Flota "1" o-- "0..*" Vehiculo : agrupa
@enduml
```

Irás aprendiendo cada flecha en los capítulos siguientes. A lo largo del curso, cada diagrama importante incluye su código PlantUML en una pestaña para que lo copies y lo pruebes.

### Por qué merece la pena

- El `.puml` es **texto**: lo guardas en el repositorio junto al código y con `git diff` ves exactamente qué cambió.
- No pierdes tiempo colocando cajas ni alineando flechas.
- Es fácil corregir y reutilizar: copiar y pegar un fragmento es más rápido que redibujar.

La contrapartida: tienes que aprender su sintaxis, y no controlas al milímetro dónde queda cada caja.

## 2.6. Otras opciones: Mermaid y herramientas CASE completas

- **Mermaid** es otro lenguaje de diagramas basado en texto, muy parecido en espíritu a PlantUML. Los diagramas de este curso están escritos con él, y plataformas como GitHub lo muestran directamente en los archivos Markdown. Más información en [mermaid.js.org](https://mermaid.js.org/).
- **Herramientas CASE completas.** Cuando se necesita generar código o hacer ingeniería inversa se suele recurrir a herramientas de modelado como **Astah UML**, **StarUML**, **Modelio** o **Papyrus** (un módulo de Eclipse). Cada una tiene su propia licencia, así que conviene comprobar las condiciones antes de elegirla: por ejemplo, Astah ofrece licencia gratuita a estudiantes con correo académico. Las veremos en el capítulo 10.

## Resumen del capítulo

- Una herramienta **CASE** asiste en alguna tarea del desarrollo; las que soportan UML van desde simples editores de dibujo hasta herramientas con repositorio de modelo, generación de código e ingeniería inversa.
- Se elige según coste, plataforma, tipos de diagrama, formato de archivo, generación de código y facilidad de uso.
- **draw.io** dibuja arrastrando símbolos: es ideal para aprender la notación.
- **PlantUML en VS Code** dibuja a partir de texto: es ideal para diagramas que viven junto al código y se versionan con Git.

## Actividades

**Actividad 1.** Instala PlantUML en VS Code y dibuja con él la clase `Conductor` (atributos privados `dni` y `nombre` de tipo `String`; operaciones públicas `getDni()` y `getNombre()`). Después dibújala también en draw.io.

??? success "Solución"
    Código PlantUML:

    ```text
    @startuml
    skinparam classAttributeIconSize 0

    class Conductor {
      - dni : String
      - nombre : String
      + getDni() : String
      + getNombre() : String
    }
    @enduml
    ```

    Y el resultado esperado en cualquiera de las dos herramientas:

    ```mermaid
    classDiagram
        class Conductor {
            -dni : String
            -nombre : String
            +getDni() String
            +getNombre() String
        }
    ```

**Actividad 2.** Elige la herramienta más adecuada en cada caso y justifica tu respuesta (draw.io, PlantUML o una herramienta CASE completa):

1. Necesitas un diagrama de clases con aspecto cuidado para una presentación, y quieres colocar cada caja donde tú decidas.
2. Quieres que los diagramas del proyecto se guarden en Git y que, al revisar una modificación, se vea qué cambió.
3. Tienes un proyecto Java de 40 clases y necesitas obtener su diagrama automáticamente.

??? success "Solución"
    1. **draw.io**: controlas la posición y el aspecto de cada elemento.
    2. **PlantUML**: el archivo es texto, así que `git diff` muestra los cambios línea a línea.
    3. **Herramienta CASE con ingeniería inversa** (o una utilidad que la ofrezca): dibujar 40 clases a mano es lento y propenso a errores.

**Actividad 3.** Guarda el archivo `coche.puml` en un repositorio Git y haz un *commit*. Después añade a la clase una operación `frenar(decremento : int) : void`, y comprueba con `git diff` qué ha cambiado.

??? success "Solución"
    ```powershell
    git init
    git add coche.puml
    git commit -m "Diagrama de la clase Coche"
    ```

    Tras añadir la operación en el archivo, `git diff` mostrará solo la línea nueva:

    ```text
    +  + frenar(decremento : int) : void
    ```

    Con un `.drawio` el mismo cambio aparecería como un bloque de XML difícil de leer. Esa es la ventaja de los diagramas en texto.
