ANEXO · MVP externo (fuera del protocolo): CPMX — Fiat On‑Ramp MXN (Bitso Polling)
Fecha: 30 de agosto de 2025
Ámbito: flujo de terceros para comprar CPMX con MXN usando cuenta personal de Bitso + n8n (polling).
Estado: MVP operativo (≈ 80% automatizado).

Importante: Este flujo es externo al protocolo. Puede requerir KYC del tercero (Bitso/PSP). El protocolo CPMX no ofrece on/off‑ramp ni solicita KYC.

1. Resumen ejecutivo
Define un flujo donde un cliente paga por SPEI y recibe CPMX on‑chain desde Tesorería mediante un contrato distributor. Objetivo: permitir que un cliente pague en MXN y reciba CPMX automáticamente sin webhooks bancarios. Automatización: ~80% (latencia típica de polling).

2. Notas
- Este anexo resume el MVP descrito en el TXT original; completar diagramas, tokens de seguridad y límites operativos en futuras versiones.

