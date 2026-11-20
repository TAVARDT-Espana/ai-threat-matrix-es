# Matriz Interactiva de Amenazas para Sistemas de Inteligencia Artificial

[![Live Demo](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-38bdf8?style=for-the-badge)](https://tavardt-espana.github.io/ai-threat-matrix-es/)
[![Standard](https://img.shields.io/badge/Standard-OWASP%20LLM%20%26%20MITRE-3b82f6?style=for-the-badge)](https://tavardt-espana.github.io/ai-threat-matrix-es/)
[![Privacy](https://img.shields.io/badge/Privacy-100%25%20Client--Side-10b981?style=for-the-badge)](https://tavardt-espana.github.io/ai-threat-matrix-es/)
[![License](https://img.shields.io/badge/License-MIT-slate?style=for-the-badge)](LICENSE)

Matriz interactiva de amenazas y guia de mitigacion para modelos de lenguaje y sistemas de IA generativa. Basado en OWASP LLM y MITRE ATLAS.

Desarrollado para organizaciones y profesionales en **Espana**, este repositorio ofrece una matriz interactiva para evaluar la postura de seguridad y generar planes de blindaje tecnico en soluciones con inteligencia artificial.

---

## Modos de Operacion

### 1. Aplicacion Web en Navegador (GitHub Pages)
Acceda a la herramienta grafica directamente desde el navegador:
- **Enlace Oficial**: [https://tavardt-espana.github.io/ai-threat-matrix-es/](https://tavardt-espana.github.io/ai-threat-matrix-es/)
- **Privacidad Total**: Procesamiento realizado 100% en el motor JavaScript de su navegador. Ningun dato arquitectonico se envia a servidores externos.

### 2. Herramienta de Linea de Comandos (CLI)
Para ejecucion automatizada en tuberias de integracion continua (CI/CD) o auditorias locales:

```bash
# Evaluacion basica indicando arquitectura de agente autonomo
python threat_matrix_evaluator.py --arch agent

# Exportacion de Blueprint de Blindaje en formato Markdown
python threat_matrix_evaluator.py --arch rag --export-blueprint hardening-blueprint.md

# Modo estricto para despliegues seguros (retorna codigo 1 ante vulnerabilidades)
python threat_matrix_evaluator.py --profile profile.json --strict

# Salida estructurada en JSON
python threat_matrix_evaluator.py --arch agent --json
```

---

## 10 Vectores de Amenaza Evaluados (OWASP Top 10 for LLMs)

1. **Inyeccion de Prompts (Directa e Indirecta)**: Manipulacion de directrices del modelo mediante entradas maliciosas o contexto externo.
2. **Divulgacion de Informacion Sensible**: Fuga involuntaria de datos confidenciales o secretos en las respuestas del sistema.
3. **Vulnerabilidades en Cadena de Suministro**: Librerias desactualizadas, complementos vulnerables o modelos sin procedencia verificada.
4. **Envenenamiento de Datos y Modelos**: Corrupcion intencionada de conjuntos de entrenamiento o bases documentales.
5. **Tratamiento Inadecuado de Salidas**: Paso de respuestas sin sanear a interpretes de codigo o motores de bases de datos.
6. **Exceso de Autonomia en Agentes**: Herramientas con permisos de ejecucion sin limites ni validacion humana.
7. **Fuga del Prompt de Sistema**: Extraccion de reglas de negocio confidenciales incluidas en el prompt base.
8. **Debilidades en Embeddings y Vectores**: Inyeccion de documentos alterados en la base vectorial para manipular la respuesta.
9. **Alucinaciones y Desinformacion Critica**: Generacion de conclusiones falsas en flujos criticos de decision operativa.
10. **Consumo Ilimitado de Recursos**: Agotamiento de capacidad computacional o sobrecostes abusivos de tokens.

---

## Integracion en GitHub Actions

```yaml
name: AI Threat Matrix Gate
on: [push, pull_request]

jobs:
  evaluate-ai-security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Instalar Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
      - name: Ejecutar Evaluacion de Amenazas en IA
        run: |
          python threat_matrix_evaluator.py --arch agent --strict
```

---

## Estandares Institucionales y Conformidad

- **Jurisdiccion**: Espana
- **Marco Tecnico**: Estandares Europeos de Seguridad en IA, OWASP LLM y MITRE ATLAS
- **Organizacion Responsable**: [TAVARDT-Espana](https://github.com/TAVARDT-Espana)

## Ecosistema y Enlaces TAVARDT

- **Portal Institucional**: [https://ag.tavardt.com/es/](https://ag.tavardt.com/es/)
- **Herramientas de Ciberseguridad**: [https://tools.tavardt.com/es/](https://tools.tavardt.com/es/)
- **Canal de Contacto Tecnico**: [https://ag.tavardt.com/es/contacto/](https://ag.tavardt.com/es/contacto/)

---

### Licencia
Distribuido bajo licencia MIT. Consulte el archivo [LICENSE](LICENSE) para mas detalles.
