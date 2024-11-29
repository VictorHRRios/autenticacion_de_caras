INSTRUCCIONES PARA CORRER EL PROYECTO

1. **Clona el repositorio**  
   Utiliza el siguiente comando para clonar el repositorio en tu máquina local:  
   git clone <URL_DEL_REPOSITORIO>

2. **Edita el archivo Dockerfile**  
   Edita el archivo `Dockerfile` cambiando el número de puerto en FLASK_RUN_PORT.

3. **Corrección en el archivo `template/index.html`**  
   Existe un error si ejecutas el proyecto en un servidor en el archivo `template/index.html` en el siguiente fragmento de código:

       const response = await fetch('/predict', {
           method: 'POST',
           body: formData // Assuming formData contains the uploaded image
       });

   Para solucionarlo, elimina el slash inicial en el endpoint de `fetch`, dejando el código de la siguiente forma:

       const response = await fetch('predict', {
           method: 'POST',
           body: formData // Assuming formData contains the uploaded image
       });
   
4. **Construye la imagen**  
   En la terminal, navega al directorio del proyecto y ejecuta el siguiente comando para construir la imagen:  
   podman build -t [Nombre del Proyecto] .

5. **Ejecuta el contenedor**  
   Una vez construida la imagen, ejecuta el contenedor con el siguiente comando:  
   podman run -p [Número de puerto]:[Número de puerto] [Nombre del Proyecto]
   
   Nota: Cambia el puerto `3029` por el puerto que desees utilizar, de acuerdo con las indicaciones de tu entorno.

