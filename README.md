
# VTA

Varias cosas suceden después de que se inicia la navegación en el enrutador: coincidencia de rutas, carga de rutas y componentes diferidos, ejecución de guardias y resolutores, por nombrar algunas. Una vez que se hayan completado con éxito, las nuevas rutas estarán listas para ser activadas. Esta activación de ruta es la actualización de DOM que queremos realizar como parte de la transición de vista.

Cuando la función de transición de vista está habilitada, la navegación se "pausa" y se realiza una llamada al método startViewTransition del navegador. Una vez que se ejecuta la devolución de llamada startViewTransition (esto sucede de forma asincrónica, como se describe en la especificación aquí), la navegación se "reanuda". Los pasos restantes para la navegación del enrutador incluyen actualizar la URL del navegador y activar o desactivar las rutas coincidentes (la actualización DOM).

Finalmente, la devolución de llamada pasada a startViewTransition devuelve una Promesa que se resuelve una vez que Angular haya terminado de renderizar. Como se describió anteriormente, esto le indica al navegador que se debe capturar el nuevo estado DOM y que debe comenzar la transición.

Las transiciones de vista son una mejora progresiva. Si el navegador no admite la API, el enrutador realizará las actualizaciones del DOM sin llamar a startViewTransition y la navegación no se animará.
