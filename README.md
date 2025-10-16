# EcoAgent IRL · Hackatón

> Agente de Telegram + plataforma de crowdfunding que coordina micro‑tareas de limpieza en espacios públicos. Pagos y contratos en **CELO** con **GoodDollar (G$)**.

## Disclaimer
Todo el código es nuevo para esta hackatón, **excepto** la parte del repositorio **irl-agents**, idea que veníamos iterando anteriormente y que adaptamos para esta edición.

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
1. Un vecino escribe al bot de Telegram.
2. El bot solicita descripción, fotos y ubicación del problema.
3. Se estima costo básico y se crea campaña de crowdfunding en la web.
4. Al alcanzar el objetivo, el sistema divide en micro‑tareas y asigna a trabajadores cercanos.
5. Los trabajadores completan, suben evidencias y el sistema verifica.
6. Se liberan pagos on‑chain en CELO usando GoodDollar.

## Arquitectura (resumen)
- **Bot de Telegram**: FastAPI/Node o Python (según repo), conexión a base de datos y colas.
- **Crowdfunding dApp**: front web + contratos CELO. Manejo de aportes en G$ y emisión de milestones.
- **IRL Engine**: asignación por geolocalización, validación de evidencia, estado de tareas.
- **Pagos**: contratos CELO + GoodDollar. Custodia sin custodia.

> Nota: detalles finos de cada módulo están en sus repos correspondientes.

## Despliegue rápido (hackatón)
> Objetivo: levantar demo funcional con los tres componentes conectados.

### 1) Bot de Telegram
- Variables de entorno sugeridas:
  - `TELEGRAM_BOT_TOKEN=`
  - `DB_URL=`
  - `CROWDFUND_BASE_URL=`
  - `IRL_ENGINE_URL=`
  - `CELO_RPC_URL=`
  - `GOODDOLLAR_TOKEN_ADDRESS=`
- Comandos típicos:
  ```bash
  # Python
  pip install -r requirements.txt
  uvicorn app:app --reload --port 8000

  # Node (si aplica)
  npm i && npm run dev
  ```

### 2) dApp de Crowdfunding + Contratos CELO
- Requisitos:
  - Node 18+
  - cuenta CELO de testnet y faucet
- Variables de entorno sugeridas:
  - `CELO_PROVIDER_URL=`
  - `PRIVATE_KEY=`
  - `GOODDOLLAR_TOKEN_ADDRESS=`
- Comandos típicos:
  ```bash
  npm i
  npm run deploy:testnet
  npm run start
  ```

### 3) IRL Engine
- Variables de entorno sugeridas:
  - `DB_URL=`
  - `STORAGE_BUCKET=`
  - `VERIFICATION_THRESHOLD=`
- Comandos típicos:
  ```bash
  pip install -r requirements.txt
  python main.py
  ```

## Contratos y Direcciones
> Añadir aquí las direcciones una vez desplegadas en testnet/mainnet.

- `CrowdfundingFactory`: `TBD`
- `Campaign`: `TBD`
- `GoodDollar (G$)`: `TBD` en CELO

## API y Endpoints clave
> Resumen mínimo para integración cruzada. Ver cada repo para docs completas.

- **Bot → dApp**: crear campaña
  - `POST /api/campaigns` `{ title, goal, location, images[] }`
- **IRL → dApp**: marcar milestone cumplido
  - `POST /api/campaigns/:id/milestones/:m/complete`
- **dApp → CELO**: `createCampaign`, `fund`, `release`

## Roadmap inmediato
- [ ] Validación básica de evidencia por imagen
- [ ] QA de pagos con GoodDollar en testnet CELO
- [ ] Listado público de campañas activas
- [ ] Panel de worker con tareas cercanas
- [ ] Scripts de despliegue unificados (Makefile o npm scripts)

## Contribuir
Pull requests y issues bienvenidos. Para cambios mayores abrir primero un issue con la propuesta.

## Licencia
Definir licencia para cada repo. Sugerencia: MIT para el bot y la dApp, revisar compatibilidad en irl‑agents.

## Agradecimientos
- Comunidad CELO y GoodDollar.
- Mentores y organizadores de la hackatón.

---

### Notas para ediciones
- Mantener este README como índice. La configuración detallada vive en cada repo.
- Al cerrar la hackatón, actualizar secciones de contratos y endpoints con valores finales.

