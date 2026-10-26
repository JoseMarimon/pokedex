## Pasos de configuración:

1. **Preparación del Repositorio:** 
   * Se subió el código fuente de Angular a un repositorio público en GitHub llamado `pokedex`.
   * Se eliminaron configuraciones obsoletas en el archivo `.yml` de GitHub Actions (como Codecov) que bloqueaban la compilación.
   * Se ajustó el archivo `environment.prod.ts` modificando la variable de las imágenes a `imagesPath: '/assets/images'` para evitar errores 404 en los sprites al pasar a producción.

2. **Creación del recurso en Azure:**
   * En el portal de Azure, se buscó el servicio **Aplicaciones web estáticas** y se seleccionó "Crear".
   * **Suscripción:** Azure for Students.
   * **Grupo de recursos:** Se creó un grupo específico para el proyecto.
   * **Región:** Debido a políticas y restricciones de la suscripción estudiantil (error *RequestDisallowedByAzure* en regiones como East US 2), se seleccionó una región aprobada (ej. **West US 2** o **West Europe**).

3. **Detalles de Implementación (GitHub):**
   * Se inició sesión con la cuenta de GitHub y se vinculó el repositorio `pokedex` seleccionando la rama `main`.

4. **Detalles de Compilación (Angular):**
   * **Valores preestablecidos:** Angular
   * **Ubicación de la aplicación:** `/` 
   * **Ubicación de la API:** *(en blanco)*
   * **Ubicación de salida:** `dist/pokedex-angular`

5. **Publicación:**
   * Al hacer clic en "Revisar y crear", Azure generó automáticamente un archivo de flujo de trabajo (`.yml`) en el repositorio de GitHub.
   * GitHub Actions ejecutó la compilación de Angular en segundo plano y desplegó los archivos estáticos generados directamente en la URL pública proporcionada por Azure.
6. **  **Configuración de Encabezados de Seguridad (HTTP Headers)**
    

Para cumplir con las políticas de seguridad y prevenir ciberataques, fue necesario configurar encabezados HTTP. En Azure Static Web Apps, esto se logra creando un archivo de configuración.

1.  En la raíz de mi repositorio, creé un archivo llamado `staticwebapp.config.json` .
    
2.  Añadí la siguiente configuración para habilitar CSP, HSTS, X-Frame-Options, entre otros
   <img width="1542" height="392" alt="image" src="https://github.com/user-attachments/assets/7dd74582-48cf-4699-94c5-c84462c491ea" />

