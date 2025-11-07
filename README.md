# IllyVoIP Security Research: Análisis de Vulnerabilidades en Servicios de VoIP

![Estado](https://img.shields.io/badge/Estado-Investigación_Completada-green)
![Entorno](https://img.shields.io/badge/Entorno-Controlado_Laboratorio-blue)
![Propósito](https://img.shields.io/badge/Propósito-Educativo_Preventivo-orange)

## 📖 Introducción

Esta investigación documenta un análisis de seguridad realizado sobre la plataforma **IllyVoIP**, demostrando vulnerabilidades críticas en servicios de telefonía IP que podrían ser explotadas por actores maliciosos para realizar ataques de suplantación de identidad (spoofing) a gran escala.

**🔒 Aviso Legal**: Todas las pruebas se realizaron en un entorno completamente controlado, con dispositivos propios, números telefónicos autorizados y consentimiento explícito de todas las partes involucradas.

## 🎯 Objetivos de la Investigación

- Analizar el proceso de registro y verificación en servicios VoIP
- Identificar vectores de ataque mediante SMS y llamadas telefónicas
- Demostrar la facilidad de suplantación de números legítimos
- Documentar medidas de protección para usuarios finales
- Concienciar sobre riesgos en comunicaciones no solicitadas

## 🛠️ Metodología de Pruebas

### 1. Registro en la Plataforma

**Captura1.png** - Proceso de registro en IllyVoIP:

- Registro con email corporativo
- **Vulnerabilidad identificada**: Posibilidad de usar datos falsos o robados
- Verificación mínima de identidad del usuario
- Sistema CAPTCHA básico que no previene registros maliciosos

### 2. Obtención de Crédito de Prueba

**Captura2.png** - Interacción con soporte:

- Apertura de ticket solicitando crédito de prueba
- Respuesta automática otorgando 1€ sin verificación adicional
- **Hallazgo crítico**: Credibilidad inmediata sin validación rigurosa

### 3. Envío de SMS Suplantados

**Carpeta `sms/`** - Pruebas de envío de mensajes:

- **Captura3.png**: Interfaz de envío con selección de número origen
- **Captura4.png**: Confirmación de envío exitoso
- **Captura5.png**: SMS recibido en dispositivo objetivo mostrando "Illyvoip" como remitente

**🔍 Hallazgos en SMS:**

- Selección libre de número origen entre múltiples países
- Posibilidad de personalizar nombre del remitente
- Envío inmediato sin verificación de propiedad del número
- Capacidad de simular entidades legítimas (bancos, servicios, etc.)

### 4. Llamadas Telefónicas Suplantadas

**Carpeta `llamadas/`** - Pruebas de suplantación en llamadas:

- **Captura6.png**: Configuración SIP y Caller ID modificable
- **Captura7.png**: Llamada recibida mostrando número suplantado

**🔍 Hallazgos en Llamadas:**

- Modificación del Caller ID en algunos escenarios
- Llamadas desde números no asociados al usuario real
- Posibilidad de explotar fallos de configuración en rutas SIP

## ⚠️ Riesgos Identificados

### Alto Impacto:

- **Smishing (SMS Phishing)**: Envío masivo de mensajes fraudulentos
- **Vishing (Voice Phishing)**: Llamadas suplantando entidades legítimas
- **Suplantación de Identidad**: Uso de números oficiales de bancos/instituciones
- **Recolección de Credenciales**: Ingeniería social avanzada

### Factores Agravantes:

- Registro con datos falsos o robados
- Verificación mínima de identidad
- Crédito inmediato sin validación
- Latencia de 24 horas antes de activación completa

## 🎭 Escenarios de Ataque Potenciales

### Caso 1: Suplantación Bancaria

```
Atacante → Registro anónimo → Solicita crédito → Envía SMS masivos
simulando banco → Redirige a phishing → Roba credenciales
```

### Caso 2: Extorsión Telefónica

```
Atacante → Configura Caller ID oficial → Realiza llamadas masivas
→ Solicita datos personales → Ejecuta fraudes
```

### Caso 3: Campaña de Desinformación

```
Atacante → Usa números legítimos → Difunde mensajes fraudulentos
→ Daña reputación de empresas → Crea caos social
```

## 🛡️ Recomendaciones de Seguridad

### Para Usuarios Finales:

- **Verificar siempre**: Contactar mediante canales oficiales conocidos
- **No confiar en Caller ID**: Los números pueden ser suplantados
- **Desconfiar de enlaces**: No hacer clic en SMS no solicitados
- **Validar identidad**: En llamadas sensibles, colgar y llamar al número oficial

### Para Proveedores de Servicio:

- Implementar verificación rigurosa de identidad
- Establecer límites estrictos para nuevos usuarios
- Monitorizar patrones de uso sospechosos
- Validar propiedad de números utilizados como origen

### Para Desarrolladores:

- Implementar autenticación multifactor
- Validar estrictamente datos de registro
- Auditar regularmente configuraciones SIP
- Monitorizar intentos de spoofing

## 🔬 Explicación Técnica: ¿Por Qué Es Posible?

### Fallos en Protocolos de Voz

Los protocolos VoIP (SIP, RTP) fueron diseñados para funcionalidad, no seguridad. La suplantación es posible debido a:

1. **Falta de Autenticación Estricta**: Muchos carriers confían en el Caller ID recibido
2. **Configuraciones Permisivas**: Routers SIP que no validan origen real
3. **Interconexión de Redes**: Diferentes niveles de seguridad entre proveedores
4. **Compatibilidad Retroactiva**: Mantener soporte para sistemas legacy

### Economía de los Servicios VoIP

La competencia agresiva lleva a proveedores a:

- Minimizar fricción en el registro
- Ofrecer pruebas gratuitas inmediatas
- Priorizar funcionalidad sobre seguridad
- Mantener precios bajos recortando controles

## 📊 Estructura del Repositorio

```
illyvoip-security-research/
│
├── README.md
├── img/
│   ├── Captura1.png          # Página de registro
│   ├── Captura2.png          # Ticket de soporte
│   ├── sms/
│   │   ├── Captura3.png      # Interfaz envío SMS
│   │   ├── Captura4.png      # Confirmación envío
│   │   └── Captura5.png      # SMS recibido
│   └── llamadas/
│       ├── Captura6.png      # Configuración llamada
│       └── Captura7.png      # Llamada recibida
└── references/
    └── video_tutorial.txt    # Enlace referencia
```

## 🚨 Conclusión y Impacto

Esta investigación demuestra la alarmante facilidad con que actores maliciosos pueden explotar servicios VoIP legítimos para realizar ataques de suplantación a escala industrial. La combinación de:

- Registro con datos falsos
- Obtención inmediata de crédito
- Capacidad de modificar Caller ID
- Ausencia de verificación rigurosa

Crea un ecosistema perfecto para el fraude telefónico. Existen cientos de servicios similares a IllyVoIP con vulnerabilidades equivalentes o peores.

## 📞 Responsabilidad Ética

Este proyecto se rigió por estrictos principios éticos:

- ✅ Consentimiento explícito de todas las partes
- ✅ Entorno 100% controlado
- ✅ Sin afectación a terceros
- ✅ Propósito educativo y preventivo
- ✅ Reporte responsable a proveedores

## 📚 Referencias

- [Video tutorial referencia](https://www.youtube.com/watch?v=4yIohOXgzAQ&t=3s)
- Documentación técnica protocolos VoIP
- Best practices OWASP para comunicaciones seguras

---

**🔐 Recordatorio**: El conocimiento aquí documentado debe usarse exclusivamente para fortalecer medidas de seguridad y protección. La reproducción de estas técnicas sin consentimiento es ilegal y éticamente reprobable.

_Última actualización: [Fecha]_
