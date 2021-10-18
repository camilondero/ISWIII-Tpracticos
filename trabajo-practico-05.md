 Trabajo Práctico 5 - Herramientas de construcción de software

4- Desarrollo:

1- Instalar Java JDK si no dispone del mismo.
  - Java 8 es suficiente, pero puede utilizar cualquier versión.
  - Utilizar el instalador que corresponda a su sistema operativo
  http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

  - Agregar la variable de entorno JAVA_HOME

2- Instalar Maven

  - Instalar maven desde https://maven.apache.org/download.cgi (última versión disponible 3.6.1)

  - En Linux/Mac se puede agregar la siguiente entrada al archivo ~/.bash_profile

        export PATH=/opt/apache-maven-3.6.1/bin:$PATH
3- Introducción a Maven

Qué es Maven?

Qué es el archivo POM?
- modelVersion
- groupId
- artifactId
- versionId

Repositorios Local, Central y Remotos http://maven.apache.org/guides/introduction/introduction-to-repositories.html

Entender Ciclos de vida de build
default
clean
site
Referencia: http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Build_Lifecycle_Basics
Comprender las fases de un ciclo de vida, por ejemplo, default:
