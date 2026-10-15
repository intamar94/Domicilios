# CLAUDE.md — FARO

Este archivo guía a Claude Code en el repositorio de FARO. Léelo entero antes de cualquier tarea.

## Qué es FARO

Marketplace local de mandados y ayuda cotidiana entre personas en Alemania.

1. El Cliente publica una necesidad.
2. FARO la valida y calcula condiciones (precio, distancia, tiempo).
3. Aparece en el marketplace.
4. Un Helfer (persona normal, no repartidor profesional) la acepta voluntariamente.
5. La ejecuta y recibe su Vergütung.

Plan maestro y estado de tareas: tablero "FARO — Tablero Maestro"
https://claude.ai/code/artifact/45bacf9a-809d-4c36-924b-ab2a4497fd7b

## Alcance

- Toda Alemania desde el inicio. Arquitectura multi-zona, preparada para más países después.
- Nada fijo a una ciudad. Todo lo regional (zonas, tarifas, horarios, idioma, moneda, reglas) es configuración, nunca código.

## MVP — qué entra y qué no

Visión: cualquier mandado cotidiano («estoy enferma y quiero algo del Lidl o de la panadería»).

ENTRA:
- RECOGER: Click & Collect ya pagado por el Cliente en la tienda.
- HACER: devolver o recoger paquetes, llaves, documentos, reparaciones.
- COMPRAR (decisión de Intamar, 15/10/2026; detalle en docs/01-investigacion/01.10): el Helfer paga con una tarjeta virtual de un solo uso por mandado, emitida por el PSP, con tope autorizado por el Cliente, ticket obligatorio y cobro del importe real. El Helfer nunca pone su dinero. Se diseña y se simula ya; con dinero real solo cuando H3 confirme por escrito la emisión de tarjetas.
- FARO cobra solo su tarifa de servicio, vía un PSP regulado.

NO ENTRA (no implementar, aunque parezca fácil):
- Que el Helfer adelante dinero propio, o que FARO compre y revenda productos.
- Saldo FARO y FARO Card.
- Medicamentos (con o sin receta), alcohol, tabaco, acompañar personas, ayuda física.

Motivo: FARO nunca toca dinero de terceros sin un proveedor regulado confirmado por escrito (ZAG / BaFin).

## Gates bloqueantes (decisiones humanas)

No escribas código que dependa de estos puntos. Si una tarea los toca, márcala BLOCKED y explica por qué.

- H1 Forma jurídica (UG) + Steuerberater.
- H2 Encuadre legal del Helfer (abogado laboral; Directiva de Trabajo en Plataformas).
- H3 PSP que confirme por escrito los pagos a Helfer y la emisión de tarjetas virtuales de un solo uso para COMPRAR.
- H4 Proveedor regulado para Saldo / FARO Card.
- H5 Seguro de responsabilidad.

Regla de diseño ligada a H2: no programes penalizaciones, sanciones automáticas ni control de horarios sobre el Helfer. Deja esos puntos como configuración desactivada y documentada.

## Stack candidato

- App Cliente y App Helfer: React Native + Expo + TypeScript.
- Backend: Supabase (PostgreSQL, Auth, Storage, Edge Functions). Row Level Security siempre activo.
- Admin (FARO Control): Next.js + TypeScript.
- Pagos: PSP regulado (pendiente de H3).
- Analítica: PostHog. Errores: Sentry. Diseño: Figma.
- Accesibilidad: WCAG 2.2 AA obligatorio.
- Identidad visual: teal, ámbar, azul profundo.

Es candidato: si una tarea exige cambiarlo, propón la alternativa con sus tradeoffs antes de cambiarlo.

## Estados de tareas

BACKLOG → READY → IN_PROGRESS → REVIEW → TESTING → APPROVED → DONE
Otros: BLOCKED, REWORK, REJECTED.

Una tarea solo pasa a DONE con su criterio de aceptación cumplido y evidencia (tests, captura, enlace).

## Fase actual: 00 Núcleo

- 00.1 Alcance del MVP — IN_PROGRESS
- 00.2 Flujo Cliente
- 00.3 Flujo Helfer
- 00.4 Estados del mandado
- 00.5 Modelo de datos v0
- 00.6 Reglas multi-zona
- 00.7 Gates LEGAL / FINANCE / SECURITY

Las 20 fases (00 Núcleo → 19 Expansión) y sus dependencias están en el tablero.

## Cómo trabajar

1. No asumas contexto que no tienes. Si falta algo, pregunta en el issue o deja la duda escrita en el PR.
2. Ediciones quirúrgicas. No reescribas archivos enteros si basta con cambiar unas líneas.
3. Expón los tradeoffs en el PR, no los escondas.
4. Cada tarea es un objetivo verificable: el PR debe pasar CI y no romper tests existentes.
5. Un issue = una tarea = un PR pequeño.
6. Commits en inglés, en formato convencional (feat:, fix:, docs:, chore:).
7. Nunca subas claves ni secretos. Usa variables de entorno.
8. Datos personales: RGPD/DSGVO. Mínimo de datos, cifrado, borrado posible.
9. Al terminar una tarea, actualiza su estado y deja en el PR qué se hizo y cómo se verificó.

## Idioma

- Código, nombres de variables y commits: inglés.
- Documentación interna: español.
- Textos de la app: alemán primero (i18n desde el inicio, preparado para más idiomas).
