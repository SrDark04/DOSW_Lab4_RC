# DOSW_Lab4_RC

## Estructura del proyecto

### 1. ¿Qué es un arquetipo (Archetype) en Maven?
Un arquetipo en Maven es una plantilla o modelo de proyecto que ya está predefinido y permite la generación rápida de la estructura del proyecto, los archivos de configuración (`pom.xml`) y los directorios necesarios para iniciar el desarrollo.

---

### 2. ¿Para qué sirve el arquetipo `maven-archetype-quickstart`?
El arquetipo `maven-archetype-quickstart` sirve para generar de manera rápida una estructura base estandarizada de un proyecto Java simple (por ejemplo, una aplicación de consola "Hola mundo"). Automatiza la creación de directorios (`src/main/java`, `src/test/java`) y el archivo de configuración `pom.xml` con las dependencias necesarias para un proyecto básico de Java.

---

### 3. ¿Cuál es el comando con el cual se puede crear un proyecto basado en un arquetipo Maven?
El comando para crear un proyecto basado en un arquetipo Maven es el siguiente:

```bash
mvn archetype:generate
```

Más específicamente, para crear un proyecto con el arquetipo `maven-archetype-quickstart`, se puede usar este comando:

```bash
mvn archetype:generate -DgroupId=com.ejemplo -DartifactId=mi-proyecto -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

---

### 4. ¿Qué es un pull request?
Un pull request (PR) o "solicitud de extracción" es una funcionalidad en plataformas de control de versiones como GitHub, GitLab o Bitbucket que permite a los desarrolladores notificar a su equipo sobre cambios realizados en una rama o en un repositorio. Sirve para solicitar que el código propuesto sea revisado y fusionado (mergeado) en la rama principal, facilitando la colaboración y la revisión de código (code review) antes de integrar nuevas funcionalidades.

---

### 5. ¿Cómo se crea un pull request?
- Crear una rama (`branch`) para realizar los cambios en el código.
- Realizar los cambios necesarios y hacer commit de esos cambios.
- Subir la rama al repositorio remoto (`push`).
- En la plataforma de control de versiones (por ejemplo, GitHub), crear un pull request desde la rama creada hacia la rama principal (`main` o `master`), proporcionando una descripción clara de los cambios realizados y solicitando la revisión del equipo.

---

### 6. ¿Cómo se aprueba un pull request?
- Un miembro del equipo revisa el pull request, verificando que los cambios sean correctos y estén alineados con los estándares del proyecto.
- Si todo está correcto, se aprueba el pull request y se fusionan (merge) los cambios en la rama principal.
- El equipo puede dejar comentarios o solicitar modificaciones si hay errores o áreas de mejora.

---

## Bibliografía
- Boutemy, H. (2010, 25 de abril). Maven quickstart archetype – maven quickstart archetype. Apache.org. https://maven.apache.org/archetypes/maven-archetype-quickstart/
- Cardellino, F. (2021, 26 de enero). Cómo hacer tu primer pull request en GitHub. freecodecamp.org. https://www.freecodecamp.org/espanol/news/como-hacer-tu-primer-pull-request-en-github/
- Crear una solicitud de incorporación de cambios. (s/f). https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request
- Fuentes, J. A. N. (2018, 24 de abril). ¿Por qué utilizar Arquetipos Maven? En Mi Local Funciona. https://www.enmilocalfunciona.io/por-que-utilizar-arquetipos-maven/
- Kulkarni, S. (2023, 23 de noviembre). DevOps tool: Maven (Build Tool). Medium. https://medium.com/@mesagarkulkarni/devops-tool-maven-build-tool-b66d31048290
