# Arquitectura del Stack de Reconocimiento en Python

El stack se estructura como un conjunto modular de herramientas independientes,
pero diseñadas para integrarse conceptualmente en un pipeline de reconocimiento
completo. Cada módulo resuelve un paso específico del proceso de asset discovery
y ataque a superficie.

## Estructura general

```
stack-recon-python/
│
├── port-scanner/             → Escaneo TCP/HTTP paralelo
├── subdomain-enumerator/     → OSINT + brute force + DNS mapping
├── eXploration/              → Recon avanzado (WAF, CDN, CORS, SSL…)
│
├── modules/                  → Reuso de utilidades
│   ├── dns_tools/
│   ├── banner_utils/
│   └── waf_fingerprints/
│
└── docs/
    ├── architecture.md
    ├── methodology.md
    └── roadmap.md
```


## Filosofía de diseño

- **Modularidad:** cada herramienta funciona sola y como parte del stack.
- **Reutilización:** funciones comunes en `/modules`.
- **Recon escalable:** pensado para targets individuales o múltiples.
- **Paralelización:** uso extensivo de ThreadPoolExecutor.
- **Enfoque realista:** basado en técnicas utilizadas en pentesting y bug bounty.

---

## Interacción entre módulos

- *Subdomain Enumerator* genera superficie → usada por *eXploration*.
- *Port Scanner* permite detectar servicios expuestos en hosts válidos.
- *eXploration* realiza fingerprinting, detección de WAF/CDN, endpoints, etc.
- *Real Origin Detection* complementa con análisis CDN bypass.
