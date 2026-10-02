# Índice

* [Elementos necesarios](#elementos-necesarios)
* [Identificar datos corruptos](#identificar-datos-corruptos)
* [Cómo eliminar datos corruptos](#cómo-eliminar-datos-corruptos)
* ["La solución habitual"](#la-solución-habitual)
* [Prevenir la corrupción de datos](#prevenir-la-corrupción-de-datos)
* [Más recursos](#más-recursos)

> **¡Haz una copia de seguridad completa de tus archivos de guardado antes de intentar cualquiera de estos pasos!**

---

# Elementos necesarios

## Carpeta de mods de Steam Workshop (Workshop Mods)

* Se puede acceder haciendo clic en el icono de carpeta de un mod de Steam Workshop en el menú de mods de Paralives.
* Navegando hasta:

**Windows:**

```text
C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
```

**Mac:**

```text
~/Library/Application Support/Steam/steamapps/workshop/content/1118520
```

## Carpeta de Paralives (Mods locales)

* Se puede acceder haciendo clic en el icono de carpeta de un mod local en el menú de mods de Paralives.
* Navegando hasta:

**Windows:**

```text
C:\Users\USER\AppData\LocalLow\Paralives\Paralives
```

**Mac:**

```text
~/Library/Application Support/com.Paralives.Paralives/
```

## Paralives\Player.Log

* Se puede leer con cualquier programa para leer archivos de texto, como Notepad o Notepad++.
* Se encuentra en la carpeta Paralives\Paralives.
* Proporciona registros de la sesión actual o de la última sesión jugada de Paralives.

## Carpeta Paralives\MySavedGames.mod

* Carpeta que contiene todas las partidas guardadas actuales y los guardados automáticos.
* Se encuentra en la carpeta Paralives\Paralives.
* Esta carpeta es más importante que cualquier otra.
* ¡Haz regularmente una copia completa de esta carpeta y guárdala en un lugar seguro fuera de los archivos del juego!

## Carpeta Paralives\MyPremadeHouseholds.mod

* Hogares guardados en la biblioteca.

## Carpeta Paralives\MyPremadeLot.mod

* Solares guardados en la biblioteca.

## Carpeta Paralives\MyPremadeOutfits.mod

* Atuendos guardados en la biblioteca.

## Carpetas Paralives\Local.mod y 0.mod

* Almacenan configuraciones del juego, como muestras de color personalizadas.

---

# Identificar datos corruptos

Los datos corruptos están compuestos por archivos que han sido modificados de modo que ya no tienen el formato o la secuencia que el juego espera encontrar.

## Archivos desactualizados

* El juego se ha actualizado y estos archivos ya no cumplen con la sintaxis actual.
* Aunque esto puede ocurrir ocasionalmente con los mods, casi todos los plugins de inyección de código de BepInEx quedan desactualizados después de una actualización del juego.
* Si hay un plugin de BepInEx instalado pero los mods siguen sin funcionar, el plugin podría estar causando más problemas de los que resuelve.

## Archivos modificados incorrectamente

* Estos archivos han sido modificados por un jugador, modder o incluso por el motor del juego y ahora son incorrectos.
* Esto ocurre cuando se utilizan mods o plugins y después se eliminan.

Por ejemplo, un mod utilizado para añadir un atuendo personalizado puede eliminarse mientras el atuendo sigue identificado en los archivos del juego.

Puede ser imposible eliminar algunos mods sin romper una partida guardada.

## Archivos movidos incorrectamente

* Los archivos suelen ser movidos por el jugador, el motor del juego o Steam, y algunas partes del archivo quedan atrás o son eliminadas.

## ¿Cómo me indicará el juego qué archivos están corruptos?

El motor del juego intentará informar al usuario cuando haya un error mediante notificaciones directas e indirectas.

### Directas:

* Ventanas emergentes en pantalla
* Notificaciones en la consola
* Eventos en player.log

### Indirectas:

* Parpadeos
* Destellos
* Tirones
* Lag
* Crashes
* Operaciones canceladas

## Leer la consola de errores y Player.Log

Los informes de la consola de errores y player.log solo se solapan parcialmente, por lo que es importante comprobar ambos al intentar identificar un error.

Es importante identificar el error inicial e ignorar los errores adicionales causados por el primer error. Al leer el registro de errores, intenta solucionar los errores de arriba abajo en orden secuencial.

Si se introducen varios errores al mismo tiempo, puede ser muy difícil diagnosticarlos. Es importante realizar solo un pequeño número de cambios entre pruebas.

Si el juego funciona correctamente, toma nota de los errores del registro para poder descartarlos posteriormente cuando algo deje de funcionar.

### CONSOLA DE ERRORES

* La consola de errores se puede abrir dentro del juego como una pestaña del menú de trucos.
* No se puede utilizar si el juego no carga.

1. Pulsa Ctrl+Shift+C para abrir el menú de trucos.
2. Pulsa la zanahoria para cambiar a la pestaña de la consola.
3. La consola está dividida en tres categorías según su importancia.
4. Solo los errores rojos son importantes para este tutorial.

### PLAYER.LOG Y PLAYER-PREV.LOG

* Este archivo registra las acciones realizadas por el motor de juego Unity que ejecuta Paralives.
* Player.log se sobrescribe cada vez que se inicia el juego y se mueve a Player-prev.log.
* Se encuentra en la carpeta de mods locales Paralives\Paralives.
* Se puede añadir más información al registro activando opciones en el panel de control. Demasiadas opciones pueden hacer que el registro aumente rápidamente de tamaño.
* Si algo del registro es importante, ¡haz una copia!

### Errores buenos (al menos no malos):

```text
+ Meta cache is expired
+ Loaded asset database (No metacache) of mod Local.mod in 0.06581748 seconds
+ The referenced script on this Behaviour (Game Object 'SlackService') is missing!
+ Serialization depth limit 10 exceeded
+ Loaded asset database of mod MyPremadeLot.mod in 0.04702377 seconds
+ Unloading 10 unused Assets to reduce memory usage
```

### Errores malos:

```text
- NullReferenceException: Object reference not set to an instance of an object
- Material builder got given parameters that don't match any shaders
- Could not resolve 'ProceduralRig/ReachWithLeftArm/ArmLChainIK/TargetArmLChainIK'
- FileNotFoundException
- Failed to find setting class
- Could not register Paralives Town.saved
```

> Nota: En la versión 1.7 hay tres nuevos errores rojos en la consola y en player.log que no parecen afectar negativamente al rendimiento del juego.
>
> * `+ System Exception: Invalid Path...`
> * `+ Runtime data is null...`
> * `+ OperationException: Addressables...`

> Nota: En la versión 1.8A, el importador .fbx no funcionaba correctamente y se quedaba atascado en la pantalla de importación de assets.

---

# Tipos de errores

Los tipos de problemas que ocurren a nivel técnico.

## Referencia nula

* A veces llamada referencia de puntero nulo.
* Cualquier error relacionado con que no se pudo encontrar una configuración, objeto, malla o valor.
* El juego hace referencia a un objeto que no puede encontrar o no entendió lo que encontró.

> Nota: El juego puede gestionar algunas referencias nulas y varias forman parte de la versión de acceso anticipado del juego.

## Fuera de límites

* El juego recibió un valor fuera del rango esperado.
* Si el juego espera un valor entre 0 y 10, pero recibe el valor 10842, puede producirse un error.

## Traducción

* El juego intentó reparar un archivo que determinó que estaba dañado y el resultado fue incorrecto.

Por ejemplo, un problema con archivos .tmp, ⁠.mod.meta y .tmp

## Sintaxis

* El juego se actualizó y el mod ya no cumple con los estándares establecidos por el juego. Es más común con los plugins de inyección de código de BepInEx.
* A algunos mods creados cuando se lanzó el juego les faltan dos puntos en el archivo de texto.

---

# Categorías de síntomas

Cuando se desconoce la causa del error, el objetivo es relacionar los síntomas con una causa específica. Después de solucionar cada error, el juego debería funcionar. Estas son categorías arbitrarias para ayudar a agrupar errores similares en conjuntos.

Es importante identificar el error inicial e ignorar los errores adicionales causados por el primer error.

## Cat A — Iniciar el juego

### Síntomas

* El juego no puede llegar al menú principal de Paralives
* La pantalla está negra
* El juego se bloquea al iniciarlo desde Steam
* Aparece un error al iniciar el juego desde Steam
* El juego se queda atascado en una imagen de nubes.

### Posibles soluciones

* Comprueba que el hardware cumpla los requisitos mínimos para jugar a Paralives.
* Un archivo crítico utilizado durante el inicio del juego está corrupto, no se puede leer o no es accesible.
* Comienza verificando los archivos del juego.
* Crea una excepción para Paralives en el antivirus.
* Comprueba player.log en la carpeta de mods locales paralives/paralives para detectar errores.

## Cat B — Importar assets

### Síntomas

* Se queda atascado al importar assets

### Posible causa

Un archivo de mod no se puede leer.

### Posibles soluciones

* Elimina los mods más recientes de la carpeta de mods locales paralives/paralives o de las carpetas de Steam Workshop hasta resolver el problema.
* Verifica los archivos del juego.

## Cat C — Seleccionar una partida

### Síntomas

* El juego vuelve al menú principal al intentar cargar una partida
* El archivo de guardado aparece en blanco

### Posible causa

El archivo de guardado tiene nombres de archivo incorrectos, le faltan archivos o no se puede leer.

### Posible solución

Comienza comprobando que el nombre de la partida coincida con los archivos meta que contiene y que la partida incluya todos los componentes necesarios.

## Cat D — Cargar una partida

### Síntomas

* El juego se queda atascado mientras carga una partida
* El juego permanece en la pantalla de carga indefinidamente

### Posible causa

Un mod corrupto, un mod eliminado incorrectamente o corrupción de la partida, como un error de referencia nula.

Puede ser imposible eliminar algunos mods sin romper una partida guardada.

### Posible solución

Comprueba si los errores persisten en una partida nueva.

## Cat E — Modo Live

### Síntomas

* El juego se queda atascado o se congela al abrir un menú en el modo Live
* El juego se queda atascado o se congela al realizar una acción específica en el modo Live

### Posible causa

Un mod corrupto, un mod eliminado incorrectamente o corrupción de la partida, como un error de referencia nula.

Puede ser imposible eliminar algunos mods sin romper una partida guardada.

### Posible solución

Comprueba si los errores persisten en una partida nueva.

## Cat F — Menús

### Síntomas

* El menú del juego no se abre al hacer clic
* El menú del juego aparece vacío al hacer clic
* El menú del juego no se cierra

### Posible causa

Un mod corrupto, un mod eliminado incorrectamente o corrupción de la partida, como un error de referencia nula.

Puede ser imposible eliminar algunos mods sin romper una partida guardada.

### Posible solución

Comprueba si los errores persisten en una partida nueva.

## Cat G — Instalar mods

### Síntomas

* Los mods no se instalan

### Posibles soluciones

* Comprueba las carpetas de mods de Steam y locales en busca de archivos incompletos.
* Elimina los archivos de mods corruptos que impidan la descarga.

## Cat H — Mods faltantes

### Síntomas

* Los mods instalados no aparecen en el menú de mods
* Los mods instalados aparecen en el menú de mods, pero no aparecen en el juego

### Posibles soluciones

* Comprueba si hay mods corruptos.
* Comprueba si hay archivos de mods duplicados.

## Cat I — Validar mods

### Síntomas

* Los objetos de mods instalados no aparecen al equiparlos a un personaje
* Los objetos de mods instalados han desaparecido
* Un personaje con objetos de mods ha desaparecido
* Los objetos de mods tienen un aspecto extraño
* Los objetos de mods interactúan de una manera inesperada
* Los objetos de mods tienen el color, la forma o el tamaño incorrectos

### Posible solución

Comprueba si hay mods corruptos.

---

> **¡Haz una copia de seguridad completa de tus archivos de guardado antes de intentar cualquiera de estos pasos!**

---

# Cómo eliminar datos corruptos

Ordenado por nivel de dificultad y complejidad.

## Fácil

### Desactivar y activar los mods

* A veces los mods no se inicializan correctamente, lo que puede solucionarse desactivando y volviendo a activar un solo mod mediante el menú de mods del juego.

### Reiniciar Paralives

* El juego cuenta con medidas de protección contra datos corruptos que se activan cuando se inicia el juego.
* Puede parecer absurdo, pero reiniciar el juego varias veces puede ser efectivo en algunos casos.

### Iniciar una nueva partida

* Si los errores son demasiado complicados o no se pueden solucionar, iniciar una nueva partida guardada puede ser la mejor opción.

### Verificar los archivos del juego o reinstalar el juego mediante Steam

* En el cliente de Steam, con el juego cerrado:

  * Steam > Paralives > Propiedades > Verificar integridad de los archivos del juego

### Volver a suscribirse a todos los mods para eliminar archivos corruptos

1. Añade todos los mods suscritos a una colección personalizada
2. Cancela la suscripción a todos los mods
3. Suscríbete a todos los mods de la colección

### Eliminar mods hasta eliminar el mod corrupto

* Elimina un mod a la vez o utiliza el método 50/50 para eliminar la mitad de los mods hasta identificar el mod corrupto.
* Los mods pueden seguir causando errores incluso cuando están desactivados. Deben eliminarse por completo moviendo, cancelando la suscripción o eliminando los archivos del mod.
* Puede ser necesario reiniciar el juego entre cada prueba para asegurarse de que se eliminen los archivos almacenados en caché.
* ¡Documenta tus resultados y anota qué mods funcionan!

### Volver a suscribirse a los mods lentamente para asegurarse de que se instalen correctamente

* La teoría es que instalar demasiados mods a la vez provoca errores, así que instala los mods lentamente.
* El juego está diseñado para instalar mods rápidamente, pero quizá haya algo de cierto en esto.

---

## Intermedio

### Mover los mods de Steam Workshop a la carpeta de mods locales Paralives\Paralives

* Los mods instalados localmente son interpretados de forma diferente por el motor del juego, lo que puede solucionar el error.
* Mientras el juego no esté ejecutándose, abre el explorador de archivos y vuelve a la carpeta de mods de Steam Workshop:

  ```text
  C:\Program Files (x86)\Steam\steamapps\workshop\content\1118520\
  ```
* Escribe ".mod" en la barra de búsqueda. Si no aparecen resultados, prueba con "*.mod".
* Esto mostrará las carpetas que contienen mods dentro de la carpeta de mods de Steam.
* Selecciona, corta y pega todas las carpetas .mod en la carpeta de mods locales Paralives\Paralives.
* Todas las carpetas deben moverse a la vez.
* Después cancela la suscripción a los mods para evitar que Steam vuelva a copiarlos.
* Asegúrate de que la copia de la carpeta de mods de Steam Workshop se haya eliminado correctamente, ya que tener dos copias del mismo mod puede causar errores.

### Eliminar cualquier archivo restante en las carpetas de mods de Steam Workshop

* Vuelve a workshop\content\1118520\ y elimina cualquier archivo que no se haya eliminado correctamente.
* Presta atención a los detalles, ya que los pequeños errores serán difíciles de encontrar más adelante.
* Es muy probable que los archivos restantes causen errores cuando el juego no los espera.

### Usar comandos de consola para reparar una partida corrupta eliminando datos corruptos

* `CLEARALLOCCUPATIONS` eliminará todos los trabajos y el historial laboral del para seleccionado y no se puede deshacer.
* `CLEARCHARACTEROUTFITS` eliminará todos los atuendos del para seleccionado y no se puede deshacer.
* `CLEARINVENTORY` vacía el inventario del para seleccionado y no se puede deshacer.
* El tutorial enlazado a continuación explica los comandos de trucos disponibles.

Tutorial de comandos de trucos ⁠Console and Cheat Commands

### Instalar un plugin de inyección de código para gestionar errores de mods

* Estos plugins funcionan dando al motor del juego más tiempo para procesar cada archivo de mod y ayudándolo a diagnosticar errores.
* Los plugins también pueden causar corrupción de datos adicional si no se mantienen y actualizan correctamente.
* Con suerte, los plugins dejarán de ser necesarios a medida que los desarrolladores de Paralives añadan más código de corrección de errores al juego.

Paralines Launcher Plugin ⁠Paraline Launcher [Help | Bug R…

---

## Avanzado

### Purgar la carpeta de mods locales

* Esto es necesario para conseguir un reinicio completamente limpio.
* Puede ser necesario desactivar Steam Cloud para evitar que los archivos corruptos se restauren durante las pruebas.

1. Corta y pega la carpeta de mods locales en un lugar seguro fuera de los archivos del juego, como el escritorio
2. Verifica los archivos del juego mediante Steam
3. Reinicia el juego. Al iniciarse, Paralives regenerará toda la carpeta de mods locales desde cero.
4. Comprueba que se haya generado una nueva carpeta de mods locales.
5. Comprueba si el problema se ha solucionado.

   * Sí: vuelve a introducir los archivos importantes de la copia realizada en el paso 1.
   * No: intenta otros métodos para solucionar el problema antes de volver a introducir archivos antiguos.
6. Añade a la carpeta Paralives recién generada únicamente archivos que se consideren seguros para reducir las posibilidades de copiar archivos de datos corruptos.

### Editar directamente los archivos de guardado para eliminar datos corruptos

* Los archivos de guardado son archivos de texto y pueden modificarse directamente.
* Se puede utilizar cualquier editor de texto, pero se recomienda Notepad++ con un plugin para formatear archivos JSON.
* El tutorial enlazado a continuación explica cómo están formateados los archivos de guardado.

Explicación de la carpeta de mods locales ⁠Mod Folder/Save Folder

### Mover partes seguras de una partida a un nuevo archivo de guardado

* Cuando no se puede identificar el problema de la partida, mueve pequeñas partes a una nueva partida.
* Este método puede ser útil para intentar identificar archivos corruptos.
* Por ejemplo, las carpetas de hogares pueden arrastrarse entre partidas con una pérdida de datos relativamente pequeña.
* El tutorial enlazado a continuación explica cómo están formateados los archivos de guardado.

Explicación de la carpeta de mods locales ⁠Mod Folder/Save Folder

### Usar comandos de consola para reconstruir personajes en una nueva partida

* Cuando todo está perdido, quizá sea mejor empezar de nuevo en una nueva partida, pero con algo de ventaja inicial.
* Se pueden utilizar comandos como `SETMONEY` para añadir dinero.
* Los comandos pueden utilizarse para restaurar habilidades, recetas y mucho más.
* El tutorial enlazado a continuación explica los comandos de trucos disponibles.

Tutorial de comandos de trucos ⁠Console and Cheat Commands

---

> **¡Haz una copia de seguridad completa de tus archivos de guardado antes de intentar cualquiera de estos pasos!**

# "La solución habitual"

El método de arrasar con todo para solucionar la mayoría de los problemas eliminando todos los archivos asociados al juego y conseguir el mejor comienzo limpio posible. No recomiendo esta solución para todos los problemas, ya que puede hacer que las partidas antiguas con mods dejen de ser jugables sin los mods de los que dependen para funcionar correctamente.

## Purgar todos los archivos del juego para empezar de nuevo

1. Purga los archivos del juego cortando y pegando toda la carpeta de mods locales paralives/paralives en el escritorio.
2. Cancela la suscripción a todos los mods de Steam Workshop y elimina cualquier archivo de mod restante.
3. Verifica los archivos del juego mediante Steam o reinstala el juego.
4. Reinicia Paralives.
5. Inicia una nueva partida.
6. Si el juego funciona ahora, revierte lentamente los cambios hasta que el problema vuelva a aparecer y sabrás cuál es la causa del problema.

---

# Prevenir la corrupción de datos

## Haz copias de TODO y CON FRECUENCIA

* Haz una copia física de los archivos importantes en un lugar seguro, como el escritorio, fuera de los archivos del juego.
* Los archivos accesibles para el motor del juego de Paralives siempre pueden corromperse.

> Nota: El comando ZIPSAVEFILE hará una copia de tu partida actual en el escritorio. Puede sobrescribir la copia anterior si el comando se utiliza dos veces.

Tutorial de comandos de trucos ⁠Console and Cheat Commands

`ZIPSAVEFILE` crea un ZIP de la partida actual en el escritorio.

## Lee las reseñas de los mods

* ¡Y deja reseñas tú también!
* Los comentarios de los mods son la forma en que los modders y otros usuarios comparten información sobre los mods.
* Si el mod parece estar roto, ¡díselo al modder para que pueda solucionarlo!

## Desactivar Steam Cloud

* Steam Cloud es excelente para proteger archivos importantes, pero a veces causa problemas difíciles de encontrar.
* A Steam Cloud le gusta recuperar archivos caducados sin avisar a nadie y simplemente colocarlos allí para que los encuentres más tarde.

## Eliminar mods correctamente

* Los mods añaden referencias de objetos al juego.
* Cada instancia de estos objetos debe eliminarse manualmente de la partida ANTES de eliminar el mod.
* Es mucho más fácil eliminar objetos de mods dentro del juego que modificando un archivo de guardado.
* ¡Elimina ese sofá elegante y ese suéter divertido antes de eliminar el mod!

## Actualizar controladores

* Para este tutorial, el controlador en el que debes centrarte es el de la tarjeta gráfica (GPU).
* En Windows, descarga la aplicación de Nvidia o AMD e instala el nuevo controlador cada pocos meses.

## Actualizar el sistema operativo

* Sí, qué asco, pero ¡es importante!
* Ejecuta regularmente el software de actualización integrado, como Windows Update.

## Instalar mods lentamente y comprobar los mods instalados individualmente o en pequeños grupos

* Esto puede ayudar al juego a procesar cada archivo sin cometer errores.

## Mantenimiento preventivo del hardware

* Cuida el ordenador y él cuidará de ti.
* Instala y ejecuta software antimalware obtenido de forma segura.
* Comprueba si hay daños físicos y limpia el polvo.
* Ejecuta programas integrados para comprobar el estado y la estabilidad de los componentes.

---

# Más recursos

## Hilos que hablan sobre problemas con mods (donde consigo mis sujetos de prueba)

* Recomendaciones de los desarrolladores para solucionar problemas
  https://steamcommunity.com/app/1118520/discussions/1/569288683937662349/
* Megahilo sobre mods faltantes
  https://discord.com/channels/595045400805769238/1517352862395404499
* Los mods no cargan
  https://discord.com/channels/595045400805769238/1517449529174130779
* Errores de referencia nula
  https://discord.com/channels/595045400805769238/1517532031662424154
* Errores de referencia nula
  https://discord.com/channels/595045400805769238/1513991069379858515/1517000216207822899
* Archivos de mods corruptos
  https://discord.com/channels/595045400805769238/1517266950944981062
* Wiki de Paralives
  https://paralives.wiki.gg/wiki/Portal:Modding_guides
* Registro de cambios de Paralives
  https://www.paralives.com/news
* Desarrollo de Paralives
  https://www.paralives.com/development
* Hoja de ruta de Paralives
  https://paralives.notion.site/f138c4f6cb234604be16fe4198d17f51
* Errores conocidos
  https://discord.com/channels/595045400805769238/1508927230154244216
* Hoja de ruta de Paralives
  https://paralives.notion.site/f138c4f6cb234be16fe4198d17f51
* Errores conocidos
  known-issues-and-bugs

