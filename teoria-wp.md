# WordPress
![WordPress](http://bextlan.com/v4/themes/v4/img/cursos/wordpress.jpg)


## Índice
1. [Slides](http://bextlan.com/slides/wordpress/)
1. [Links importantes sobre WP](#links-importantes-sobre-wordpress)
1. [Taxonomía de WP](#taxonomía-de-wordpress)
1. [Instalación de WP](#instalación-de-wordpress)
1. [Importación / Exportación de WP](#importación--exportación-de-wordpress)
1. [Temas en WP](#temas-en-wordpress)
1. [The Loop](#the-loop)
1. [Plantillas en WP](#plantillas-en-wordpress)
1. [Hooks en WP](#hooks-en-wordpress)
1. [Plugins en WordPress](#plugins-en-wordpress)
1. [Widgets en WordPress](#widgets-en-wordpress)


## Links importantes sobre WordPress
* [WordPress.org](http://wordpress.org)
* [WordPress.com](http://wordpress.com)
* [WordPress.org en Español](http://es.wordpress.org)
* [WordPress.com en Español](http://es.wordpress.com)
* [Empezando con WordPress](https://codex.wordpress.org/es:Getting_Started_with_WordPress)
* [Codex WordPress](http://codex.wordpress.org/)
* [Developers WordPress](https://developer.wordpress.org/)
* [Embeds](https://codex.wordpress.org/Embeds)
* [Roles y Capacidades en WordPress](https://codex.wordpress.org/es:Roles_y_Capacidades#Subscriber)
* [Tabla de Roles y Capacidades en WordPress](https://codex.wordpress.org/Roles_and_Capabilities#Capability_vs._Role_Table)
* [Buenas Prácticas de PHP en WordPress](https://make.wordpress.org/core/handbook/coding-standards/php/)
* [Recuperar passwords de Usuarios WordPress](http://www.wpbeginner.com/beginners-guide/how-to-reset-a-wordpress-password-from-phpmyadmin/)
* [Herramienta para resetear passwords de Usuarios WordPress](http://pajhome.org.uk/crypt/md5/)

**[⬆ regresar al índice](#Índice)**


## Taxonomía de WordPress
Es la forma en como WP estructura el contenido de nuestro sitio y lo hace a través de:
* Categorías
* Etiquetas
* Entradas
* Páginas

### Categorías (Clasifican el contenido)
Son la tabla de contenidos de tu sitio web. Son utilizadas para agrupar tus contenidos y mantener una clasificación.

Deben ser la base de la organización ya que conservan un orden jerárquico, y podemos generar sub-categorías.

### Etiquetas (Palabras clave, para búsquedas internas)
Se utilizan como microdatos que describen detalles específicos del contenido.

Sirven como keywords para el SEO de nuestras publicaciones.

### Entradas (Publicaciones)
Es el contenido final de nuestras páginas o secciones, pueden tener asociadas más de una categoría, si no le especificamos una, se guardaran como parte de la categoría que trae WP por defecto "Sin Categoría". Podemos agregarles tantas etiquetas como sean necesarias.

### Páginas (Contenido estático)
Son contenidos que difícilmente van a cambiar, por ejemplo la sección de contacto o acerca, no se pueden asociar a categorías ni a etiquetas

### Ejemplos de Taxonomías:

	Taxnomía de Sitio de Perros
		Home(loop)
		El Perro(p)
		Comportamiento(p)
		Sentidos(p)
		Videos(p)
		Razas(c)
		En esta categoría podrás encontrar una clasificación de los perros, basada en su tamaño.
			Gigantes(sc)
			Esta categoría esta destinada a los perros gigantes.
				Bobtail(e)
				Dogo de Burdeos(e)
				Gran Danés(e)
				Mastín Napolitano(e)
				San Bernardo(e)
				Terranova(e)
			Grandes(sc)
			Esta categoría esta destinada a los perros grandes.
				Boxer(e)
				Dálmata(e)
				Dóberman(e)
				Husky Siberiano(e)
				Labrador(e)
				Pastor Alemán(e)
			Medianos(sc)
			Esta categoría esta destinada a los perros medianos.
				Basset Hound(e)
				Beagle(e)
				Border Collie(e)
				Bull Dog(e)
				Cocker Spaniel(e)
				Staffordshire Bull Terrier(e)
			Pequeños(sc)
			Esta categoría esta destinada a los perros pequeños.
				Bichón(e)
				Chihuahua(e)
				Pug(e)
				Schnauzer(e)
				Xoloitzcuintle(e)
				Yorkshire(e)
			Sin Raza(sc)
			Esta categoría esta destinada a los perros sin raza.
				Únicos(e)

	Taxonomía Sitio Bextlan v4
		Home (loop)
		Cursos (c)
			Responsive Design (e)
			jQuery (e)
			WordPress (e)
			Node.JS (e)
		Tutoriales (c)
			HTML5(e)
			JS(e)
			PHP(e)
			AS3(e)
			Vlog(e)
		Acerca (p)
		Servicios (p)
		FAQ's (p)
		Anualidad (p)

	Taxonomía Sitio mejorenvo.com
		Inicio (loop)
		Series(c)
			Temporadas (e)
		Películas(c)
			Película (e)
		FAQ(p)
		Manuales(p)
		Contacto(p)

	Taxonomía Sitio mundoheroes.net
		Home(loop)
		VideoClips(p)
		ReporteFallos(p)
		Series(c)
			Serie(e)
		Películas(c)
			Película(e)
		Comics(c)
			Comic(e)
		Marvel(et)
		DC Comics(et)
		Otras(et)

**[⬆ regresar al índice](#Índice)**


## Instalación de WordPress
1. Descargar WordPress http://es.wordpress.org/
2. Descomprimir WordPress en el localhost
3. Buscar archivo wp-config-sample.php, renombrarlo como wp-config.php y editar: 
	* db
	* user
	* pwd
	* host
	* charset
	* table_prefix
	* Authentication Unique Keys
4. Crear una  BD en MySQL desde http://localhost/phpmyadmin
5. Ejecutar la carpeta del sitio en el navegador y llenar la información de la instalación
6. Una vez instalado:
	* Para ver wp como user:
		* localhost/ruta-del-sitio
	* Para ver wp como admin:
		* localhost/ruta-del-sitio/wp-login.php
		* localhost/ruta-del-sitio/wp-admin

**[⬆ regresar al índice](#Índice)**


## Importación / Exportación de WordPress
Esto sirve para ir del localhost al servidor en internet o viceversa

1. Respaldar todo WordPress (wp-admin,wp-includes,wp-content,archivos sueltos)
2. Cargar/Descargar el respaldo (FTP, SSH, Git)
3. Exportar en formato .sql la BD desde el phpMyAdmin
	* Considera que a veces phpMyAdmin no nos agrega la instrucción CREATE DATABASE y USE
4. Abrir el archivo .sql y reemplazar todas las rutas locales a las del servidor en internet o viceversa con ayuda del comando buscar y reemplazar de tu editor de código favorito
5. Modificar las rutas de las siguientes lineas del archivo .htaccess:
	* **RewriteBase**
	* **RewriteRule**

	~~~~~~~~~~~~~~~~~~~~~~~~~~~~
	# BEGIN WordPress
	<IfModule mod_rewrite.c>
		RewriteEngine On
		RewriteBase /perros/
		RewriteRule ^index\.php$ - [L]
		RewriteCond %{REQUEST_FILENAME} !-f
		RewriteCond %{REQUEST_FILENAME} !-d
		RewriteRule ./perros/index.php [L]
	</IfModule>
	# END WordPress
	~~~~~~~~~~~~~~~~~~~~~~~~~~~~

6. Modificar BD,USER,PWD y HOST MySQL en el archivo wp-config.php
7. Importar la BD en el destino y cargar el nuevo contenido

**Nota:**
* Si las estructuras de carpeta se respetan en el servidor y en el localhost, cuando haya nuevos cambios, sólo hay que hacer los pasos 2,3, 4 y 7. los demás sólo la primera vez.
* Para seguir con el curso usaremos el tema y la base de datos del sitio WordPress que podrán encontrar en el siguiente [repositorio](https://github.com/jonmircha/perros-inicial)

**[⬆ regresar al índice](#Índice)**


## Temas en WordPress
Un Tema WordPress es una colección de archivos que trabajan juntos para producir un interfaz gráfica con un diseño unificado para el sitio. Estos archivos se llaman archivos de plantilla

Un tema modifica el modo en que el sitio es mostrado, sin modificar el código fuente de WordPress

Los temas pueden incluir archivos de plantilla personalizados, archivos de imagen, hojas de estilo, scripts (.php o .js), así como cualquier otro archivo necesario

#### Archivos Básicos de un Tema:
* **index.php**	plantilla principal
* **style.css** hoja de estilos principal del tema
* **screenshot.png** imagen representativa del tema en el administrador de WP

#### Estructura Básica de un Tema
![Estructura Básica de un Tema en WP](http://bextlan.com/img/para-cursos/estructura-tema.png)

#### Links y Funciones Básicas de un Tema:
* [Temas](https://wordpress.org/themes/)
* [Theme Forest](http://themeforest.net/)
* [Función bloginfo()](https://codex.wordpress.org/Function_Reference/bloginfo)
* [Función get_header()](https://codex.wordpress.org/Function_Reference/get_header)
* [Función get_footer()](https://codex.wordpress.org/Function_Reference/get_footer)
* [Función get_sidebar()](https://codex.wordpress.org/Function_Reference/get_sidebar)
* [Función get_template_part()](https://codex.wordpress.org/Function_Reference/get_template_part)

#### Funciones de inclusión obligatorias:
Si queremos que nuestro tema permita el correcto funcionamiento de plugins de terceros, debemos activar las siguientes funciones de esta manera WordPress permite a los plugins imprimir información en el header o el footer

* [Función wp_head()](https://codex.wordpress.org/Plugin_API/Action_Reference/wp_head) debe colocarse antes de `</head>`
* [Función wp_footer()](https://codex.wordpress.org/Plugin_API/Action_Reference/wp_footer) debe colocarse antes de `</body>`

**[⬆ regresar al índice](#Índice)**


## The Loop
**The Loop** es el código PHP usado por WordPress para mostrar las publicaciones

	if( have_posts() ):
		while( have_posts() ):
			the_post();
			//post info
	else:
		//no posts
	endif;

#### Links y Funciones relacionados con The Loop
* [The Loop](https://codex.wordpress.org/The_Loop)
* [Función have_posts()](https://codex.wordpress.org/Function_Reference/have_posts)
* [Función the_post()](https://codex.wordpress.org/Function_Reference/the_post)
* [Función the_title()](https://codex.wordpress.org/Function_Reference/the_title)
* [Función the_permalink()](https://codex.wordpress.org/Function_Reference/the_permalink)
* [Función the_date()](https://codex.wordpress.org/Function_Reference/the_date)
* [Función the_time()](https://codex.wordpress.org/Function_Reference/the_time)
* [Función the_excerpt()](https://codex.wordpress.org/Function_Reference/the_excerpt)
* [Función the_category()](https://codex.wordpress.org/Function_Reference/the_category)
* [Función the_tags()](https://codex.wordpress.org/Function_Reference/the_tags)
* [Función the_author()](https://codex.wordpress.org/Function_Reference/the_author)
* [Función the_content()](https://codex.wordpress.org/Function_Reference/the_content)
* [Función rewind_posts()](https://codex.wordpress.org/Function_Reference/rewind_posts)
* [Función query_posts()](https://codex.wordpress.org/Function_Reference/query_posts)
* [Búsquedas Personalizadas en WP](http://www.anieto2k.com/2008/01/13/query_posts-personalizando-nuestros-blogs/)
* [Parámetros para Búsquedas Personalizadas](https://codex.wordpress.org/Class_Reference/WP_Query#Parameters)
* [Función get_the_title()](https://codex.wordpress.org/Function_Reference/get_the_title)
* [Función get_the_permalink()](https://codex.wordpress.org/Function_Reference/get_the_permalink)
* [Función get_the_date()](https://codex.wordpress.org/Function_Reference/get_the_date)
* [Función get_the_time()](https://codex.wordpress.org/Function_Reference/get_the_time)
* [Función get_the_excerpt()](https://codex.wordpress.org/Function_Reference/get_the_excerpt)
* [Función get_the_category_list()](https://codex.wordpress.org/Function_Reference/get_the_category_list)
* [Función get_the_tag_list()](https://codex.wordpress.org/Function_Reference/get_the_tag_list)
* [Función get_the_author()](https://codex.wordpress.org/Function_Reference/get_the_author)
* [Función get_the_content()](https://codex.wordpress.org/Function_Reference/get_the_content)

**[⬆ regresar al índice](#Índice)**


## Plantillas en WordPress
Son los archivos que nuestro tema va utilizando dependiendo del contenido solicitado, los cuales pueden ser:

* **index.php**	plantilla principal
	* **home.php**	plantilla del home del sitio
	* **archive.php** plantilla de categorías y etiquetas
		* **category.php** plantilla de categorías
		* **tag.php** plantilla de etiquetas
	* **singular.php** plantilla de entradas y páginas
		* **single.php** plantilla de entradas
		* **page.php** plantilla de páginas estáticas
	* **404.php** plantilla para error 404
	* **search.php** plantilla para búsquedas
	* **comments.php** plantillas para los comentarios
	* **author.php** plantillas para mostrar la página de autor
* Templates personalizados:
	* Podemos tener templates personalizados para: 
		* Categorías
		* Etiquetas
		* Páginas estáticas
	* Podemos crear templates personalizados por:
		* slug
		* id

![Estructura de carpetas de un Tema en WP](http://bextlan.com/img/para-cursos/plantillas-secciones-separadas.png)

#### Links y Funciones relacionados con Plantillas
* [Estructura de Archivos de un tema en WP](http://blog.eamexicano.com/wordpress/wordpress-tema/)
* [Jerarquía de Plantillas en WP](https://developer.wordpress.org/themes/basics/template-hierarchy/)
* [Plantillas de Categorías](https://codex.wordpress.org/Category_Templates)
* [Plantillas de Etiquetas](https://codex.wordpress.org/Tag_Templates)
* [Plantillas de Páginas](https://codex.wordpress.org/Pages#Page_Templates)
* [Plantilla de Página 404](https://codex.wordpress.org/Creating_an_Error_404_Page)
* [Función get_the_author_id()](http://codex.wordpress.org/get_the_author_id)
* [Función get_the_author_meta()](http://codex.wordpress.org/get_the_author_meta)
* [Función get_the_author_posts_url()](http://codex.wordpress.org/get_the_author_posts_url)
* [Función get_the_author_posts()](http://codex.wordpress.org/get_the_author_posts)
* [Función get_avatar()](http://codex.wordpress.org/get_avatar)
* [Gravatar](http://es.gravatar.com/)
* [Función comments_template()](https://codex.wordpress.org/Function_Reference/comments_template)
* [Función comment_form()](http://codex.wordpress.org/comment_form)
* [Función wp_list_comments()](http://codex.wordpress.org/wp_list_comments)
* [Función get_search_form()](https://codex.wordpress.org/Function_Reference/get_search_form)
* [Función get_search_query()](https://codex.wordpress.org/Template_Tags/get_search_query)

**[⬆ regresar al índice](#Índice)**


## Hooks en WordPress
El archivo **functions.php**  es como una biblioteca personal de funciones, es una manera fácil de agregar o modificar el comportamiento por defecto de WordPress. Se comporta exactamente igual que un plugin, añadiendo características y funcionalidad a un tema, y se puede utilizar tanto para definir nuevas funciones PHP como para modificar las que ya incorpora WordPress, se dividen en:
* Filtros
* Acciones

#### Links y Funciones relacionados con Hooks
* [Glosario de WP](https://codex.wordpress.org/Glossary)
* [API de Plugin de WP](http://codex.wordpress.org/Plugin_API)
* [API de Hooks de WP](http://codex.wordpress.org/Plugin_API/Hooks)
* [Filtros de WP](http://codex.wordpress.org/Plugin_API/Filter_Reference)
* [Acciones de WP](http://codex.wordpress.org/Plugin_API/Action_Reference)
* [Función add_action()](https://codex.wordpress.org/Function_Reference/add_action)
* [Función add_filter()](https://codex.wordpress.org/Function_Reference/add_filter)
* [Función add_theme_support()](https://codex.wordpress.org/Function_Reference/add_theme_support)
* [Función the_post_thumbnail()](https://codex.wordpress.org/Function_Reference/the_post_thumbnail)
* [Función get_the_post_thumbnail()](https://codex.wordpress.org/Function_Reference/get_the_post_thumbnail)
* [Función register_nav_menus()](https://codex.wordpress.org/Function_Reference/register_nav_menus)
* [Función wp_nav_menu()](https://codex.wordpress.org/Function_Reference/wp_nav_menu)

**[⬆ regresar al índice](#Índice)**

## [Plugins](https://wordpress.org/plugins/) en WordPress
* [Jetpack](https://wordpress.org/plugins/jetpack/)
* [Yoast SEO](https://wordpress.org/plugins/wordpress-seo/)
* [WP Super Cache](https://wordpress.org/plugins/wp-super-cache/)
* [Contact Form 7](https://wordpress.org/plugins/contact-form-7/)
* [Comments Evolved for WordPress](https://wordpress.org/plugins/gplus-comments/)
* [WP PageNavi](https://wordpress.org/plugins/wp-pagenavi/)
* [Infinite Scroll](http://www.infinite-scroll.com/)
* [Max Mega Menu](https://wordpress.org/plugins/megamenu/)
* [Meta Box](https://metabox.io/)
* [Insert PHP](https://wordpress.org/plugins/insert-php/)
* [WP No Category Base](https://wordpress.org/plugins/wp-no-category-base/)
* [WP No Tag Base](https://wordpress.org/plugins/wp-no-tag-base/)

**[⬆ regresar al índice](#Índice)**


## [Widgets](https://codex.wordpress.org/Widgets_API) en WordPress
* [Función register_sidebar()](https://codex.wordpress.org/Function_Reference/register_sidebar)	
* [Función dynamic_sidebar()](https://codex.wordpress.org/Function_Reference/dynamic_sidebar)

**[⬆ regresar al índice](#Índice)**