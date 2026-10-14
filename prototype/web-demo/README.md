# Prototipo web de FARO (demo)

Prototipo clicable, en alemán, del flujo del Cliente (00.2) y del Helfer (00.3), con una parte de los estados de 00.4.

- **Enlace:** https://claude.ai/artifact/1xXXBpfYV2aiAHnyVhsfmZ (privado; quien vaya a probarlo necesita que se le comparta).
- **Datos:** base de datos compartida del artefacto (colección `errands`). Si no está disponible, usa el almacenamiento local del navegador (modo offline, un solo dispositivo).
- **Qué hace:**
  - El Cliente publica un mandado (categorías de 00.1, checklist de «ya pagado» y «sin artículos prohibidos», precio de ejemplo) y ve su estado y su PIN.
  - El Helfer elige su zona (código postal y alcance), ve solo los mandados de esa zona y sin direcciones exactas, acepta (con bloqueo para que dos personas no acepten el mismo), recoge, marca «no realizable» o suelta el mandado sin penalización, y entrega con el PIN o con el comprobante de la devolución.
  - Cada persona elige su nombre visible. Cliente y Helfer se ven el nombre y tienen un chat del mandado (con respuestas rápidas) mientras está en curso.
  - El formulario se adapta a la categoría (etiquetas, código, tamaño, texto de «ya pagado»). Pide día y hora con al menos 30 minutos de margen, y el mandado caduca solo si nadie lo acepta a tiempo.
  - Los mandados de ejemplo enseñan su PIN al Helfer y se confirman solos al entregarlos.
- **Mapa 3D (botón «Karte 3D»):** barrios en hexágono por código postal, con estilo de maqueta tipo Blender (three.js r128 desde cdnjs, OrbitControls desde jsDelivr). El Helfer ve chinchetas ámbar con el número de mandados abiertos y el faro marca su zona; al tocar un barrio, la lista se filtra. El Cliente ve cuántos Helfer hay **registrados** en cada barrio (colección `helfers`, sin nombre). **Nunca se muestran posiciones exactas ni quién está conectado** (decisión de Intamar, 14/10/2026: zonas aproximadas, por DSGVO y H2). Sin WebGL, quedan los chips de barrios como alternativa accesible.
- **Qué no hace (a propósito):** pagos reales (H3), registro, fotos de evidencia, mapa real de calles (la página no puede cargar imágenes externas), avisos, incidencias de entrega ni reclamaciones.
- **Limitación de privacidad:** en el prototipo todos los datos del mandado (incluido el PIN) están en un documento compartido. En la app real, las direcciones exactas y los códigos van en tablas separadas protegidas con RLS (00.5).
- **Para probarlo a solas:** se pueden aceptar los propios mandados desde «Ich helfe».

No es la app definitiva. La app real se hará con React Native + Expo y Supabase (Fases 08–10).
