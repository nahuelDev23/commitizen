Aquí tienes una guía básica para la instalación y uso de **Commitizen** en tu proyecto para que puedas hacer commits de forma más consistente y estandarizada:

### 1. Instalación de Commitizen

1. **Instala Commitizen como dependencia de desarrollo:**

   En el directorio raíz de tu proyecto, ejecuta:

   ```bash
   npm install commitizen --save-dev
   ```

2. **Configura Commitizen con un adaptador** (usaremos el adaptador de "Conventional Commits" como ejemplo):

   ```bash
   npx commitizen init cz-conventional-changelog --save-dev --save-exact
   ```

   Esto hará dos cosas:
   - Añadirá el adaptador `cz-conventional-changelog`, que sigue la convención de "Conventional Commits".
   - Actualizará el archivo `package.json` para incluir una referencia a Commitizen, con lo siguiente:

   ```json
   "config": {
     "commitizen": {
       "path": "./node_modules/cz-conventional-changelog"
     }
   }
   ```

### 2. Uso básico de Commitizen

1. **Para hacer un commit usando Commitizen**:

   En lugar de usar `git commit`, utiliza el comando:

   ```bash
   npx cz
   ```

   Esto abrirá un asistente interactivo que te guiará a través de los siguientes pasos:
   - **Tipo de cambio**: Selecciona el tipo de commit que estás haciendo, como `feat`, `fix`, `chore`, etc.
   - **Ámbito (scope)**: Especifica la parte del código afectada, como `ui`, `api`, etc. (opcional).
   - **Mensaje corto (short description)**: Escribe un mensaje corto y descriptivo para tu commit.
   - **Mensaje largo (long description)**: Si es necesario, añade detalles adicionales al commit.
   - **Referencias a tickets o issues**: Si estás trabajando en un issue específico, puedes referenciarlo aquí.
   - **Información de breaking changes**: Si tu commit introduce un cambio importante o "breaking change", puedes especificarlo.

2. **Para añadir todos los archivos y hacer un commit en una sola línea**:

   Si quieres añadir todos los archivos y luego hacer el commit con Commitizen, usa:

   ```bash
   npx cz -a
   ```

   El flag `-a` añadirá todos los archivos al área de preparación (stage) antes de hacer el commit.

### 3. Ejemplo de uso

Supongamos que hiciste algunos cambios en el código y quieres hacer un commit siguiendo la convención.

1. Ejecutas:

   ```bash
   npx cz
   ```

2. Commitizen te hará las siguientes preguntas interactivas:

   - **Select the type of change**: seleccionas `feat` (si añadiste una nueva funcionalidad).
   - **What is the scope of this change**: puedes escribir algo como `auth` (si el cambio es en el sistema de autenticación) o dejarlo vacío.
   - **Write a short description**: escribes algo como `add user login functionality`.
   - **Provide a longer description of the change**: puedes escribir detalles adicionales o dejarlo vacío.
   - **Are there any breaking changes**: si no hay cambios importantes, dejas esto vacío.
   - **Does this commit affect any open issues**: si estás trabajando en un issue, puedes referenciarlo (ej. `#123`).

   Esto generará un commit que se verá algo así:

   ```bash
   feat(auth): add user login functionality
   ```

### 4. Integración con Husky

Para garantizar que todos los commits sigan la convención, puedes integrar **Husky** para ejecutar Commitizen o **Commitlint** en los hooks de Git.

1. **Instala Husky**:

   ```bash
   npm install husky --save-dev
   ```

2. **Inicializa Husky**:

   ```bash
   npx husky install
   ```

3. **Añade un hook pre-commit** que use Commitlint para validar los mensajes de commit:

   ```bash
   npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
   ```

   Esto garantizará que tus mensajes de commit sigan las convenciones especificadas en tu configuración de Commitlint.

### 5. Otras herramientas complementarias

- **Commitlint**: Si deseas validar los mensajes de commit manualmente, puedes usarlo junto con Commitizen.
- **Lint-staged**: Puedes combinar esto con Husky para ejecutar linters solo en los archivos que están siendo añadidos al commit.

### 6. Ejemplos  de Scope 

1. **auth**: Cambios relacionados con la autenticación de usuarios (login, registro, permisos).
2. **api**: Cambios en la API, ya sea del backend o del frontend.
3. **ui**: Modificaciones en la interfaz de usuario.
4. **database**: Cambios en la base de datos (esquemas, migraciones).
5. **docs**: Actualización de documentación.
6. **config**: Cambios en archivos de configuración del proyecto (como `webpack.config.js`, `eslint`).
7. **tests**: Cambios o adiciones de pruebas automatizadas.
8. **ci**: Cambios en la integración continua o scripts relacionados con CI/CD (como configuraciones de Jenkins, GitHub Actions).
9. **build**: Cambios en el proceso de construcción del proyecto o en las dependencias externas.
10. **styles**: Cambios relacionados con los estilos (CSS, SASS, LESS).
11. **deps**: Actualización o eliminación de dependencias del proyecto.
12. **security**: Cambios relacionados con aspectos de seguridad (parches de vulnerabilidades).
13. **performance**: Mejoras de rendimiento.
14. **i18n**: Cambios relacionados con la internacionalización o localización del proyecto.
15. **routing**: Cambios en el enrutamiento de la aplicación (front o back).
16. **error-handling**: Cambios en la forma en que se manejan errores en el código.
17. **logging**: Cambios o adiciones de logging en la aplicación.
18. **notifications**: Cambios relacionados con notificaciones (push, email, etc.).
19. **webpack**: Cambios en la configuración de Webpack o en el bundle de la aplicación.
20. **nextjs**: Cambios específicos a la estructura o configuración de un proyecto en Next.js.

### Resumen

Con **Commitizen**, puedes hacer que tus commits sigan una convención clara y bien estructurada, como los "Conventional Commits". Esto es muy útil para proyectos colaborativos y para generar automáticamente changelogs a partir de los mensajes de commit.

Usando el comando `npx cz`, tendrás un asistente interactivo que te guiará para asegurarte de que cada commit sea consistente y claro.


