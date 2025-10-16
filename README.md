# EcoAgent IRL · Hackatón

> Agente de Telegram + plataforma de crowdfunding que coordina micro‑tareas de limpieza en espacios públicos. Pagos y contratos en **CELO** con **GoodDollar (G$)**.

## Disclaimer
Todo el código es nuevo para esta hackatón, **excepto** la parte del repositorio **irl-agents**, idea que veníamos iterando anteriormente y que adaptamos para esta hackaton


## Repos y Componentes
- **Agente de Telegram** · orquestación y UX conversacional: `ecoAgent`  
- https://github.com/filippello/ecoAgent
- **Web de Crowdfunding + Contratos** · CELO + GoodDollar  
- https://github.com/Sixela33/celo#
- **Herramienta IRL** · planificación, asignación y verificación  (iteración previa, terminada e integrada con GoodDollar, CELO y la plataforma de crowdfunding)
- https://gitlab.com/irl-agents

---

## Qué es EcoAgent IRL
EcoAgent IRL permite que cualquier persona reporte un problema cívico sencillo de limpieza, junte fondos en minutos y contrate a alguien cercano para resolverlo. El agente de Telegram guía el proceso, orquesta tareas, verifica con fotos y libera pagos on‑chain.

pero esto solo es el princicio, la idea es expandirlo a mas distintas tareas, la limpiezsa es un ejemplo del potencial, pero podriamos tener donaciones para contruccion de servicios basicos, reparacionesm ayudas especificas..


**Use case de esta versión:** limpieza de espacios públicos (veredas, plazas, carteles, contenedores, micro‑basurales pequeños).


## Cómo funciona (flujo)
1. Un miembro de la comunidad se contacta con nuestro agente mediante telegram @ecoagentetestbot, y puede describir el problema que esta teniendo.

<img width="879" height="245" alt="image" src="https://github.com/user-attachments/assets/430e4e05-7c33-4bde-98c5-7d3be6d0a624" />

2. El bot solicita descripción, fotos y ubicación del problema.
3. Se estima costo básico y se crea campaña de crowdfunding en la web https://crowdfund.irl-agents.xyz/
4. Al alcanzar el objetivo, el sistema divide en micro‑tareas y asigna a trabajadores cercanos.

<img width="1038" height="403" alt="image" src="https://github.com/user-attachments/assets/07035395-059e-4364-9215-6af6ce171f05" />

5. Los trabajadores se conectan con la miniapp de telegram que abre nuestra app de IRL mediante @irl_agents_bot cuando les llega la tarea la pueden completan, suben evidencias y el sistema verifica.
6. Se liberan pagos on‑chain en CELO usando GoodDollar.

<img width="652" height="279" alt="image" src="https://github.com/user-attachments/assets/50098c1a-a4f3-4cd8-b596-285c7fec549c" />





## Arquitectura (resumen)
- **Bot de Telegram**: FastAPI/Node o Python (según repo), conexión a base de datos y colas.
- **Crowdfunding dApp**: front web + contratos CELO. Manejo de aportes en G$ y emisión de milestones.
- **IRL Engine**: asignación por geolocalización, validación de evidencia, estado de tareas.
- **Pagos**: contratos CELO + GoodDollar. Custodia sin custodia.

> Nota: detalles finos de cada módulo están en sus repos correspondientes.


## sistema de verificacion
algunas tareas requieren que no solo se verifique automaticamente, en estos casos se genera en la tarea el rol de verificador, el cual es una persona que se encarga de validar las tareas realizaddas


<img width="675" height="299" alt="image" src="https://github.com/user-attachments/assets/27e60a7b-d59d-4464-9161-bd5027de259b" />

esto tambien nos permite generar reputacion en los usan nuestra app

<img width="638" height="384" alt="image" src="https://github.com/user-attachments/assets/f6d9ab72-1b22-48f0-a8f9-5a0bf0ec6ef8" />


## REPUTACION Y CURRICULUM

mucho del trabajo informal que se realiza en latam no queda registrado, con esta herramienta podemois empezar a registrar tareas, ofrecer capacitacion y mejorar la gente que trabaje para que puedan mejorar, realizando capacitaciones yy realizando tareas necesarias.

