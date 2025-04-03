# PPS-Unidad3Actividad5-Angel
Explotación y Mitigación de Cross-Site Scripting (XSS)


Objetivos:

* Investigr cómo se pueden realizar ataques de Cross-Site Scripting (XSS)
* Conocer las diversas formas de ataque XSS
* Analizar el código de la aplicación que permite ataques de Cross-Site Scripting (XSS)
* Implementar diferentes modificaciones del código para aplicar mitigaciones o soluciones.

---

## ¿Qué es XSS?
Cross-Site Scripting (XSS) es una vulnerabilidad de seguridad en aplicaciones web que ocurre cuando un atacante inyecta código malicioso en una página web que no valida ni sanitiza scripts maliciosos y que se ejecutarán en el navegador de otros usuarios.

Tipos de XSS: 

* Reflejado: Se ejecuta al hacer la solicitud con un payload (desde la URL)
* Almacenado: El script se guarda en la base de datos y afecta a otros usuarios al acceder a la página.
* DOM-Based: El código malicioso se inyecta directamente en la estructura DOM del navegador sin que pase por el servidor.


---
## Actividades

* Lee detenidamente la sección de Cross-Site Scripting de la página de PortWigger <https://portswigger.net/web-security/cross-site-scripting>

* Lee el siguiente [documento sobre Explotación y Mitigación de ataques de Inyección SQL](./files/ExplotacionYMitigacionXSS.pdf) de Raúl Fuentes. Nos va a seguir de guía para aprender a explotar y mitigar ataques de inyección XSS Reflejado en nuestro entorno de pruebas.
 
* También y como marco de referencia, tienes [ la sección de correspondiente de ataque XSS reglejado de la **Proyecto Web Security Testing Guide** (WSTG) del proyecto **OWASP**.](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/07-Input_Validation_Testing/01-Testing_for_Reflected_Cross_Site_Scripting).


--- 

### Código vulnerable

Creamos un archivo llamado comment.php en /www/

~~~
<?php
if (isset($_POST['comment'])) {
	echo "Comentario publicado: " . $_POST['comment'];
}
?>
<form method="post">
	<input type="text" name="comment">
	<button type="submit">Enviar</button>
</form>
~~~

El código malicioso anterior muestra un formuladio donde el usuario puede introducir comentarios en un campo de texto.
En el momento en que el usuario envía el formulario, el comentario introducido se muestra por pantalla con el siguiente mensaje: "Comentario publicado: \[comentario\]". 







