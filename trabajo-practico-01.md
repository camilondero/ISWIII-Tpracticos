Trabajo Práctico 1 - Git Básico
1.  Instalar Git
Baje e instale el cliente git desde  https://git-scm.com/ y baje e instale el cliente visual, TortoiseGit. 

2. Crear un repositorio local y agregar archivos.

Creamos una carpeta para nuestro repositorio y lo inicializamos.
	
	mkdir IngSoft3 
	git init
	
Agregar un archivo Readme.md, agregar algunas líneas con texto a dicho archivo.
	
	echo tp 1 ingenieria de software III > Readme.md
	
	
3. Crear un repositorio remoto
	Creamos una cuesta en git, luego creamos nuestro repositorio llamado 'ISWIII-Tpracticos'. 
	Con este comando asociamos nuestro repositorio local a nuestro repositorio remoto de github:
	
		git remote add origin  https://github.com/camilondero/ISWIII-Tpracticos.git 
		
	Para subir nuestros cambios locales al repositorio debemos agregar los cambios realizados con los comando: 
		
		git add . 
		git commit -m "primer commit"  
		git push -u origin main. 
	
4. Familiarizarse con el concepto de Pull Request
Explicar que es un pull request.
		
Un pull request es una petición para integrar nuestras propuestas o cambios de código a un proyecto.
Un pull request es una petición que el propietario de un fork de un repositorio hace al propietario del repositorio original para que este último incorpore los commits que están en el fork.
	
Crear un branch local y agregar cambios a dicho branch.

Utilizamos este commit para crear otra rama:
	
	git branch branch1 
y con este comando nos paramos en esa rama: 

	git checkout branch1
Despues, agregamos una nueva linea de texto al archivo Readme.md
		
Subimos los cambios a branch1, con esta serie de comandos:
	
	git status
	git add .
	git commit -m "new branch"
	git push origin branch1

Y luego creamos el pull request y hacemos el merge:
		
![Image text](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/PR%201.png)
![Image text](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/PR2.png)
![Image text](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/PR3.png)


5. Mergear código con conflictos
Clonamos el repositorio en otro directorio con el siguiente comando:
	
	git clone https://github.com/camilondero/ISWIII-Tpracticos.git
	
En el clon inicial, modificamos el Readme.md agregando más texto. Luego, hacemos un  commit y subir el cambio a main a github.
			
	git checkout main
	git status
	git add .
	git commit -m "Nueva linea en Readme"
	git push origin main
	
En el segundo clon también agregamos texto, en las mismas líneas que se modificaron el punto anterior.
	
Intentar subir el cambio, haciendo un commit y push. Mostrar el error que se obtiene.
	
	git add .
	git commit -m "nueva linea de texto"
	git push origin main
	
Este es el error devuelto por línea de comandos: 

![Image text](https://github.com/camilondero/ISWIII-Tpracticos/blob/main/Images/Error.png)
	
	
Hacer pull y mergear el código (solo texto por ahora), mostrar la herramienta de mergeo como luce.
	
	

Resolver los conflictos del código.

	
	
Explicar las versiones LOCAL, BASE y REMOTE.

Pushear el cambio mergeado.
