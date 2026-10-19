# Chatbot sistema experto – Sistema de reserva de habitación en hotel
LNV319 · Infraestructura de Negocio · Universidad De La Salle Bajío · Equipo 1

Chatbot "Check-In" del Hotel Real Bajío, hecho en Twine (Harlowe) con 5 niveles de solicitud.
**Demo:** https://eneascv27.github.io/chatbot-hotel/

## Niveles
1. Inicio: Reservar habitación · Consultar tarifas · Servicios del hotel
2. Tipo de habitación: Sencilla · Doble · Suite
3. Huéspedes: 1 o 2 · 3 a 6 · Más de 6 (desvío a Eventos)
4. Noches: 1 a 2 · 3 a 6 · 7 o más (desvío a Estancia larga)
5. Cierre: Confirmar reserva · Hablar con un humano · Cancelar y volver al inicio

El resumen final usa variables `(set:)` (`$hab`, `$huesp`, `$noches`).

## Base de conocimiento (reglas SI–ENTONCES)

| # | SI | ENTONCES | ¿Por qué? |
|---|----|----------|-----------|
| 1 | Más de 6 huéspedes | Desviar a Eventos / ejecutivo | Los grupos requieren varias habitaciones, tarifa negociada y posible salón; es una venta de mayor valor. *(Implementada)* |
| 2 | 7 noches o más | Desviar a Estancia larga con asesor | Se aplica tarifa mensual con descuento que no debe prometer un bot. *(Implementada)* |
| 3 | Cliente elige "Hablar con un humano" | Mostrar contacto de recepción | Evita perder la venta y frustrar al cliente. *(Implementada)* |
| 4 | Habitación Sencilla y más de 2 huéspedes | Sugerir Doble o Suite | La capacidad de la sencilla es de 2 personas; evita sobreocupación y quejas. |
| 5 | Reserva de menos de 24 h de anticipación | Confirmar por teléfono con recepción | Hay que verificar disponibilidad en tiempo real y evitar overbooking. |
| 6 | Cliente pide factura | Canalizar a administración | Requiere datos fiscales; un error trae problemas con el SAT. |

## Reflexión de negocio
1. **¿Qué proceso automatiza?** La captura de solicitudes de reserva (tipo de habitación, huéspedes y noches) y las consultas repetitivas de tarifas y servicios que hoy atiende recepción por teléfono o WhatsApp.
2. **¿Qué indicador mejoraría?** El tiempo de respuesta al cliente y la tasa de conversión de consulta a reserva, porque se responde las 24 horas y no se pierden solicitudes fuera del horario de recepción.
3. **¿Cuándo escalar a un humano y por qué?** Grupos de más de 6 personas y estancias de 7 noches o más (el costo de un error en tarifa es alto), quejas o emergencias (empatía) y solicitudes de factura o cambios de última hora (riesgo de overbooking y errores fiscales).
4. **¿Qué usuario no encuentra su opción y cómo se atiende?** El huésped que quiere modificar o cancelar una reserva existente, o el que viaja con mascota o necesita accesibilidad. Se atienden con la opción "Hablar con un humano", disponible en las ramas de desvío y en el cierre, y el equipo debería agregar esas opciones al nivel 1 en una siguiente versión.

## Contenido del repositorio
`index.html` · archivo Archive de Twine · `mapa-decision.jpg` (foto del mapa de decisión) · `README.md`
