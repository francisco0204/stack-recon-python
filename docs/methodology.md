# Metodología del Stack de Reconocimiento

Este stack sigue una metodología utilizada en equipos profesionales de Red Team
y Bug Bounty Recon, basada en etapas de descubrimiento, enumeración, fingerprinting
y validación.

## Pipeline de Recon

1. **Asset Discovery**
   - Identificación inicial del dominio objetivo.
   - Mapeo de ASNs, DNS, infra.

2. **Subdomain Enumeration**
   - OSINT (crt.sh, OTX, ThreatMiner)
   - FUZZ y brute force
   - Correlación de resultados

3. **DNS Infrastructure Mapping**
   - Resolución global distribuida
   - Comparación de resolvers
   - Detección de inconsistencias

4. **Port & Service Scanning**
   - Detección de puertos abiertos
   - Banner grabbing
   - Identificación de tecnologías base

5. **Web Recon & Fingerprinting**
   - Detection WAF/CDN
   - CORS misconfigurations
   - SSL certificate mapping
   - JS endpoint extraction
   - Sensitive paths

6. **Origin Exposure Detection**
   - Cloudflare bypass heuristics
   - ASN validation
   - Direct IP probing

## Objetivo

Crear una suite completa de herramientas que permitan entender a fondo
una infraestructura web y su superficie de ataque real.
