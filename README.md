# EcoAgent IRL · Hackatón

> Agente de Telegram + plataforma de crowdfunding que coordina micro‑tareas de limpieza en espacios públicos. Pagos y contratos en **CELO** con **GoodDollar (G$)**.

## Disclaimer
Todo el código es nuevo para esta hackatón, **excepto** la parte del repositorio **irl-agents**, idea que veníamos iterando anteriormente y que adaptamos para esta hackaton

- Telegram agent: https://github.com/filippello/ecoAgent
- Web de crowdfunding y contratos en CELO para GoodDollar: https://github.com/Sixela33/celo#
- Herramienta IRL (iteración previa, terminada e integrada con GoodDollar, CELO y la plataforma de crowdfunding): https://gitlab.com/irl-agents

---

## Qué es EcoAgent IRL
EcoAgent IRL permite que cualquier persona reporte un problema cívico sencillo de limpieza, junte fondos en minutos y contrate a alguien cercano para resolverlo. El agente de Telegram guía el proceso, orquesta tareas, verifica con fotos y libera pagos on‑chain.

**Use case de esta versión:** limpieza de espacios públicos (veredas, plazas, carteles, contenedores, micro‑basurales pequeños).

## Repos y Componentes
- **Agente de Telegram** · orquestación y UX conversacional: `ecoAgent`  
  Repositorio: https://github.com/filippello/ecoAgent
- **Web de Crowdfunding + Contratos** · CELO + GoodDollar  
  Repositorio: https://github.com/Sixela33/celo#
- **Herramienta IRL** · planificación, asignación y verificación  
  Repositorio: https://gitlab.com/irl-agents

## Cómo funciona (flujo)
1. Un miembro de la comunidad se contacta con nuestro agente mediante telegram @ecoagentetestbot, y puede describir el problema que esta teniendo.
2. El bot solicita descripción, fotos y ubicación del problema.
3. Se estima costo básico y se crea campaña de crowdfunding en la web https://crowdfund.irl-agents.xyz/
4. Al alcanzar el objetivo, el sistema divide en micro‑tareas y asigna a trabajadores cercanos.
5. Los trabajadores se conectan con la miniapp de telegram que abre nuestra app de IRL mediante @irl_agents_bot cuando les llega la tarea la pueden completan, suben evidencias y el sistema verifica.
6. Se liberan pagos on‑chain en CELO usando GoodDollar.


<img width="879" height="245" alt="image" src="https://github.com/user-attachments/assets/430e4e05-7c33-4bde-98c5-7d3be6d0a624" />


<img width="1038" height="403" alt="image" src="https://github.com/user-attachments/assets/07035395-059e-4364-9215-6af6ce171f05" />


<img width="708" height="532" alt="image" src="https://github.com/user-attachments/assets/eeafd00a-6407-4612-8baa-4238e75fb7ab" />

<img width="719" height="499" alt="image" src="https://github.com/user-attachments/assets/055f1c82-6421-4334-86cd-d1662e4f5402" />




## Arquitectura (resumen)
- **Bot de Telegram**: FastAPI/Node o Python (según repo), conexión a base de datos y colas.
- **Crowdfunding dApp**: front web + contratos CELO. Manejo de aportes en G$ y emisión de milestones.
- **IRL Engine**: asignación por geolocalización, validación de evidencia, estado de tareas.
- **Pagos**: contratos CELO + GoodDollar. Custodia sin custodia.

> Nota: detalles finos de cada módulo están en sus repos correspondientes.

## Despliegue rápido (hackatón)
> Objetivo: levantar demo funcional con los tres componentes conectados.
---

### Notas para ediciones
- Mantener este README como índice. La configuración detallada vive en cada repo.
- Al cerrar la hackatón, actualizar secciones de contratos y endpoints con valores finales.

