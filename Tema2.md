## Tema 2: Estructura de un proyecto

### Carpeta Layot
Contedrá los archivos que contienen vistas de las actividades o fragmentos.

### Carpetas Mipmap y drawable
Se relacionan directamente con la densidad de pantalla en la que se ejecutará nuestra aplicación.
En la carpeta **drawable** colocaremos todas las imagenes que vaya a usar nuestra aplicación, mientras que en la carpeta **mipmap** únicamente colocaremos el icono de la app.

### Carpeta Values
Dentro de esta carpeta por defecto tendremos tres archivos: **colors, strings y themes**.

### Acceder a los Recursos en Android desde Kotlin
Para obtener la referencia de un recurso, es necesario asignarle un identificador que lo diferencia e indica donde se encuentra.
Cada identificador se encuentra en la clase **R**, una clase generada automáticamente por el SDK. Cada recurso de la carpeta **res** es una clase anidada estática del archivo **R.class**.
Por ejemplo:

	- Para acceder al subdirectorio drawable: R.drawable.
	- Para acceder al contenido de una imagen cuyo identificador es ic_launcher_background: R.drawable.ic_launcher_background.
	- Para acceder a todos los recursos de android, podremos obtener una instancia dentro de la actividad con el método getResources:
  
~~~Kotlin
	val color = resources.getColor(android.R.color.holo_blue_bright,theme)
~~~

### Acceder desde XML
Usaremos la sintaxis: **@tipoRecurso/nombreRecurso**
~~~XML
	android:text="@string/hola_mundo"
~~~

### Android Manifest
Contiene nodos descriptivos sobre las características de la App, características como: la versión del SDK, los permisos para ejecutar algunos servicios, activitys, etc. 
En pocas palabras muestra una descripción de toda nuestra aplicación.
El nodo raíz es la etiqueta `<manifest>` y por obligación tiene que tener un hijo del tipo `<application>`.

---

**Etiqueta application**

	- **allowBackup:** (boolean) nos permite indicar si nuestra aplicación sera persistente al cerrar el AVD.
	- **icon:** indica donde está situado el icono que se usará en nuestra app.
	- **label:** indica el nombre de la aplicación que verá el usuario en su teléfono.
	- Dentro de `<application>` encontraremos expresada la actividad principal que definimos al crear el proyecto mediante la etiqueta `<activity>`.
  
---

***Etiqueta activity***

	- **label:** hace referencia al texto que mostrará la cabecera de la activity.
	- **android:name:** especifica el nombre de la actividad, por ejemplo MainActivity.
	- **android:screenOrientation:**  define si la orientación de la app será vertical u horizontal, por defecto se usará la que el dispositivo tenga predeterminada.


En Android no existe un único punto de entrada a nuestra app, puede tener varios y ser llamados desde distintas activitys.
Para especificar a que intento reaccionará nuestra app, existe la etiqueta `<intent-filter>`, que tiene dos elementos:
	- **`<action>`:** indicamos una actividad, la cual será un punto de entrada a nuestra aplicación
	- **`<category>`:** indicamos que queremos que esta actividad se añada al lanzador de la aplicación.
~~~XML
	<activity android:name=".MainActivity">
		<intent-filter>
			<action android:name="android.intent.action.MAIN"></action>
			<category android:name="android.intent.category.LAUNCHER"></category>
		</intent-filter>
	</activity>
~~~
---
***Etiqueta uses-permissions***
Android restringe los recursos de sistema de la tarjeta SD, Wi-Fi, Audio, etc.
Gracias a esta etiqueta, especficiamos los permisos que necesitara nuestra app para poder 
	
