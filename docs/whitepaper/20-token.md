PARTE II · Token CPMX

1. Resumen ejecutivo
CPMX es un token de utilidad para pagos en comercios y transferencias P2P sin gas (bajo cupo), con bajo costo total para comercios y deflación por quema directa ligada al uso real.
Tarifa al comercio (0.50% on‑chain):
● 0.20% → Fondo de Gas (el usuario no ve gas en comercios).
● 0.30% → quema directa de CPMX cobrado como tarifa en cada pago.

P2P: gas subsidiado con cuota diaria por usuario cuando el Fondo de Gas tiene excedente. Si no hay cupo, la wallet muestra “Cuenta inactiva hoy (P2P sin cupo)”.

Listado inicial: pool DEX con 5% del supply + USDC equivalente. LP bloqueado 18 meses.

1. Problema y oportunidad
Los comercios pequeños requieren bajo costo total y cero complejidad técnica. Los usuarios quieren pagar desde el móvil sin gas visible ni comisiones ocultas. CPMX resuelve ambas fricciones con un modelo simple, transparente y auditable on‑chain, enfocado en México y extensible a LatAm.

Problemas adicionales que resuelve CPMX (impacto estratégico)
● Fragmentación de pagos en LatAm: QR + wallet, costo total 0.50% on‑chain; swap a USDC opcional.
● Exclusión financiera: wallet con passkey/PIN; P2P on‑chain con cupos.
● Sostenibilidad del gas: fondo autofinanciado (0.20%); P2P sólo con excedentes.
● Transparencia: dashboard público (GMV, quema, runway).
● Lealtad abierta: descuentos opcionales interoperables.
● Riesgo regulatorio: utilidad clara de pagos; protocolo sin KYC.

2. Propuesta de valor
● Usuarios: pagos sin gas en comercios; P2P con gas subsidiado bajo cupo.
● Comercios: 0.50% on‑chain con gas incluido; panel claro; swap on‑chain a stablecoins.

5.4 P2P con gas subsidiado
● Colchón mínimo: runway ≥ 12 semanas para pagos a comercios.
● Excedente a P2P: sólo el sobrante sobre el colchón subsidia P2P.
● Cuota diaria por usuario (según runway):
○ 12–<16 semanas: 1 envío/día, tope $150 MXN.
○ 16–<20 semanas: 2 envíos/día, tope $200 MXN.
○ 20–<24 semanas: 3 envíos/día, tope $250 MXN.
○ ≥24 semanas: 5 envíos/día, tope $300 MXN.
● Sin cupo: la wallet muestra “Cuenta inactiva hoy (P2P sin cupo)” y bloquea el envío.
● P2P: sin fee; sólo gas cubierto si hay cupo.
● Conversión de topes P2P: “Los topes expresados en MXN se convierten a CPMX usando el precio de referencia de la Sección 3.1 con tolerancia ±1% y edad ≤ 10 min.”
● Expiración de firma/precio: “Si la firma expira (>10 min) o el precio se desvía >1% al ejecutar, la tx se rechaza y la app recalcula.”

5.5 Deflación (quema directa)
El 0.30% del GMV cobrado se quema en el mismo bloque. La escasez crece con el uso real, sin compras en mercado ni impuestos por transferencia.

6. Listado inicial y/o venta permissionless (sin KYC)
● Opción A — Listado directo en DEX: pool inicial con 5% del supply + contraparte en USDC. Precio fijado por el mercado. Sin whitelist, sin formularios, sin KYC.
● Opción B — LBP/Subasta abierta on‑chain: acceso permissionless sin registro.
● Compradores: no se aplican esquemas de desbloqueo individuales.
● Equipo/asesores: vesting on‑chain y verificable.
● Límites por wallet: si se usan, son reglas del contrato, no identidad.
● KYC/AML: fuera del protocolo; si un tercero on/off‑ramp lo exige, aplica su política.
Precio de referencia: se comunica en MXN como referencia informativa, liquidando en CPMX según pricing del punto 3.1.

7. Liquidez y mercados
● DEX inicial: par CPMX/USDC (Polygon).
● Depósito inicial del pool: 5% del supply = 5,000,000 CPMX + USDC equivalente al precio de referencia de arranque.
● Reserva de liquidez: 15% del supply para profundizar el pool post‑listado.
● LP bloqueados: 18 meses (plazo exacto). Locker por defecto: Team Finance; fallback Unicrypt. Al listar, se publicará dirección del LP y tx del lock en el dashboard.
● Operación de mercado: sin buybacks; la deflación proviene exclusivamente de la quema directa 0.30%.

8. Tesorería y política financiera
Tesorería bajo multisig 3/5 con límites diarios y timelock. Usos permitidos: gas, seguridad, grants de integración, auditorías, observabilidad. Prohibido explícitamente comprar CPMX en mercado. Reportes mensuales públicos.

9. Gobernanza y transparencia
● Multisig 3/5: fundador, comercio ancla, inversor, 2 independientes.
● Parámetros gobernables: reparto del 0.50% (dentro de rangos), niveles/caps P2P, límites del Paymaster/relayer, parámetros de pricing de referencia.
● Rangos duros en contrato: tarifa total 0.30–0.80%; split 0.10–0.40% Gas y 0.20–0.60% Burn.
● Timelock on‑chain: ≥ 7 días para cualquier cambio de tarifas o cupos.
● Límite de cambio por propuesta: ±0.10% en fee_total y ±0.05% en cada split.
● Dashboard público: transacciones, GMV, runway del fondo de gas, quemas, salud del relayer, wallets y parámetros.

10. Seguridad
Librerías probadas, pruebas automatizadas, auditoría externa de contratos periféricos antes de mainnet, circuit‑breakers por fallo de oráculos o picos de gas, límites por comercio/usuario y monitoreo continuo.

Almacenamiento y recuperación de claves
● Las claves se guardan cifradas con WebCrypto en el dispositivo.
● Passkeys son el factor primario; el PIN funciona como respaldo offline.
● Backups cifrados opcionales con frase de recuperación y exportación segura.
● En la ruta ERC‑4337, la recuperación social es opcional mediante guardianes.

10.1 Controles sin KYC (anti‑abuso y cupos P2P)
● Cupos por wallet + enfriamientos por patrón sospechoso.
● Enfriamiento operativo: 24–72 h (por defecto 48 h).
● Cap global por día del Fondo de Gas a nivel contrato.
● Device binding suave: huella de dispositivo y límite por combinación wallet‑dispositivo.
● Depósito simbólico reembolsable: 50 CPMX para activar cupos altos tras 14 días de buen uso.
● Listas de riesgo on‑chain mínimas: si una wallet recibe múltiples flags, baja su cupo.
● Nada de esto es “KYC”; son controles de abuso con caducidad documentada.

11. Cumplimiento (MX) y legal
● Naturaleza: token de utilidad para pagos; no otorga derechos patrimoniales ni promete rendimientos a minoristas.
● KYC/AML: no requerido por el protocolo. Si un tercero on/off‑ramp lo exige, aplica su propia política.
● Fiscal: facturación a cargo del comercio.
● Aviso legal: no es oferta de valores ni asesoría financiera/legal; cumplir regulación aplicable.

12. Ruta de producto y operaciones
● Fase 1 (0–6 semanas): pagos, relayer, Fondo de Gas, dashboard, pool CPMX/USDC (5% supply) y primera quema.
● Fase 2 (2–3 meses): +2 comercios, swap a stablecoins en la wallet, campañas con caps/KPIs.
● Fase 3 (4–6 meses): 5 comercios, ≥ 1,000 pagos/mes, ajuste de cupos P2P según salud del fondo.

13. KPIs de éxito
● Mes 1: ≥ 100 pagos; runway gas ≥ 12 semanas; dashboard en línea.
● 90 días: ≥ 300 pagos; 2 comercios; 500 wallets con tx.
● 6 meses: 5 comercios; ≥ 1,000 pagos/mes; retención ≥ 60%; quema mensual creciente.

14. Comunidad (20%) — lineamientos
Usos: boosts por comercio (4–6 semanas), referidos con uso real, vouchers/becas, bounties de contenido e integraciones. Desembolsos por KPI, verificación ligera y caps por wallet/campaña.

15. Riesgos y mitigación
Riesgo | Mitigación
--- | ---
Picos de gas/congestión | Colchón ≥ 12 semanas; ajuste dinámico; pausas de contingencia
Baja adopción | Promos por comercio; campañas con caps; referidos con prueba de uso
Volatilidad | Swap opcional a stablecoins; pricing de referencia con límites de desviación
Dump oportunista | Vesting de equipo/asesores; transparencia de distribuciones; límites en programas
Regulatorio | Utility claro; protocolo sin KYC; asesoría local
Operativo/seguridad | Auditorías; multisig; timelock; límites y monitoreo

16. Glosario
● GMV: volumen bruto procesado.
● Runway de gas: semanas cubiertas para pagos a comercios.
● TWAP/mediana de precio: referencias de precio on‑chain para cálculo de CPMX en punto de venta; no se usan para compras en mercado.
● Cupo P2P: envíos diarios subsidiados por usuario según salud del fondo.

17. Parámetros por defecto
● Tarifa comercio: 0.50% → 0.20 gas / 0.30 quema.
● Colchón de gas: ≥ 12 semanas.
● Cuotas P2P: 1–5 envíos/día según runway; topes $150–$300 MXN; tope mensual sugerido $5,000 MXN.
● Pool inicial: 5% del supply + USDC a precio de referencia.
● Listado: DEX permissionless; sin buybacks.

17 bis. Parámetros y fórmulas publicables
● Runway del Fondo de Gas:
undefined
con Costo_promedio_gas_por_pago = gasUsed × gasPrice × px(POL/MXN) y tabla de sensibilidad para tickets de 100, 300 y 1,000 MXN.

Sensibilidad de costos de gas (bajo/medio/alto)
Costo gas por pago (MXN) 0.05 | 0.08 | 0.15
Ticket 100 (Ingreso Gas 0.20) | Margen 0.15 | Margen 0.12 | Margen 0.05
Ticket 300 (Ingreso Gas 0.60) | Margen 0.55 | Margen 0.52 | Margen 0.45
Ticket 1,000 (Ingreso Gas 2.00) | Margen 1.95 | Margen 1.92 | Margen 1.85

Regla operativa: el 0.20% actúa como buffer. Si el Margen GasFund < 25% del ingreso de Gas por pago, gobernanza reduce cupos P2P hasta recuperar margen.

● Fórmulas por transacción (pagos a comercio)
La quema se ejecuta en vivo en cada pago a comercio dentro del contrato de pagos, sin impuestos por transferencia en el token.
Sea A_CPMX el monto bruto del pago en CPMX:
• Fee total: fee_total = 0.005 × A_CPMX
• Quema: burn = 0.003 × A_CPMX
• Fondo de gas: gasfund = 0.002 × A_CPMX
• Neto al comercio: A_neto = A_CPMX − fee_total
Unidades: CPMX en todas las variables. Para reporteo en valor, puede usarse un precio de referencia P = MXN/CPMX documentado en la Sección 3.1.

● Deflación esperada (agregada mensual)
Burn_mensual_CPMX = 0.003 × GMV_mensual_en_CPMX
Donde GMV_mensual_en_CPMX es la suma de A_CPMX de todos los pagos a comercios liquidados on‑chain durante el mes.
Equivalente para reportes en MXN (opcional): Burn_mensual_MXN = 0.003 × GMV_mensual_en_MXN, con GMV_mensual_en_MXN = Σ A_CPMX × P_t usando el precio de referencia por transacción o un TWAP diario, según lo indicado en la Sección 3.1.
Nota: estas expresiones son de reporte. La quema ocurre per‑tx y es auditable on‑chain en tiempo real.

18. Ejemplo numérico (100 CPMX)
● Pago a comercio: usuario envía 100 → comercio recibe 99.50; 0.20 a Fondo de Gas; 0.30 se quema.
● P2P (con cupo): emisor envía 100 → receptor recibe 100; gas cubierto; cuenta contra su cuota.
● P2P (sin cupo): “Cuenta inactiva hoy (P2P sin cupo)”; envío bloqueado.

19. Contacto y actualizaciones
Sitio y dashboard se publicarán con direcciones on‑chain y parámetros vigentes. Cambios al whitepaper se versionarán con historial público.
Aviso final: participar implica riesgos tecnológicos, operativos y de mercado. No constituye asesoría ni oferta de valores.

