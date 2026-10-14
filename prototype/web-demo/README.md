# Prototipo web de FARO (demo)

Prototipo clicable, en alemán, del flujo del Cliente (00.2) y del Helfer (00.3), con una parte de los estados de 00.4.

- **Enlace:** https://claude.ai/artifact/1xXXBpfYV2aiAHnyVhsfmZ (privado; quien vaya a probarlo necesita que se le comparta).
- **Datos:** base de datos compartida del artefacto (colección `errands`). Si no está disponible, usa el almacenamiento local del navegador (modo offline, un solo dispositivo).
- **Qué hace:**
  - El Cliente publica un mandado (categorías de 00.1, checklist de «ya pagado» y «sin artículos prohibidos», precio de ejemplo) y ve su estado y su PIN.
  - El Helfer ve la lista sin direcciones exactas, acepta (con bloqueo para que dos personas no acepten el mismo), recoge, marca «no realizable» o suelta el mandado sin penalización, y entrega con el PIN o con el comprobante de la devolución.
- **Qué no hace (a propósito):** pagos reales (H3), registro, fotos de evidencia, mapas, avisos, incidencias de entrega, reclamaciones ni expiración automática.
- **Limitación de privacidad:** en el prototipo todos los datos del mandado (incluido el PIN) están en un documento compartido. En la app real, las direcciones exactas y los códigos van en tablas separadas protegidas con RLS (00.5).
- **Para probarlo a solas:** se pueden aceptar los propios mandados desde «Ich helfe».

No es la app definitiva. La app real se hará con React Native + Expo y Supabase (Fases 08–10).
