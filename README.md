# Investigación de Seguridad: Análisis de Spoofing en SMS y Llamadas VoIP

<div align="center">

![Estado](https://img.shields.io/badge/ESTADO-COMPLETADO-success)
![Entorno](https://img.shields.io/badge/ENTORNO-LABORATORIO_CONTROLADO-informational)
![Licencia](https://img.shields.io/badge/LICENCIA-EDUCATIVA-blue)
![Plataforma](https://img.shields.io/badge/PLATAFORMA-IllyVoIP-orange)

</div>

## Resumen Ejecutivo

Esta investigación de seguridad se centra en el análisis de vulnerabilidades críticas en servicios de telefonía IP, específicamente en la plataforma IllyVoIP. El estudio demuestra cómo actores maliciosos pueden explotar estas vulnerabilidades para realizar ataques de suplantación de identidad a través de SMS y llamadas telefónicas. Todo el proceso de investigación se llevó a cabo en un entorno completamente controlado, utilizando exclusivamente dispositivos y números telefónicos propios o con consentimiento explícito, manteniendo en todo momento un estricto código ético y con fines puramente educativos y de concienciación en ciberseguridad.

## Metodología de Investigación

El proceso de investigación comenzó con el registro en la plataforma IllyVoIP, donde se pudo observar que el sistema permite el registro con datos personales sin una verificación rigurosa de identidad. Este primer hallazgo ya revela una vulnerabilidad significativa: la posibilidad de que un atacante utilice información falsa o robada para crear una cuenta a nombre de otra persona sin mayores obstáculos.

Tras completar el registro, se siguió el procedimiento documentado abriendo un ticket de soporte para solicitar el crédito de prueba de 1 euro que ofrece la plataforma. La respuesta del equipo de soporte fue inmediata y sin verificaciones adicionales, otorgando el crédito solicitado sin cuestionar la identidad del usuario o el propósito del uso. Es importante destacar que, aunque el crédito se acredita instantáneamente, la plataforma impone una restricción de 24 horas antes de permitir el uso completo de los servicios, lo que parece ser una medida anti-fraude básica pero insuficiente.

## Análisis de Vulnerabilidades en SMS

Una vez activada la cuenta completamente, se procedió a evaluar la funcionalidad de envío de SMS. La interfaz de usuario permite seleccionar entre una amplia gama de números telefónicos de diferentes países y operadoras, todos disponibles para uso inmediato sin verificación adicional. Durante las pruebas controladas, se envió un SMS desde uno de estos números al dispositivo móvil personal, utilizando un mensaje simple de "Saludos" para verificar el funcionamiento.

Los resultados obtenidos son alarmantes desde una perspectiva de seguridad. El SMS llegó al teléfono mostrando "Illyvoip" como remitente, pero la verdadera preocupación radica en la capacidad de personalizar este campo. Un atacante podría fácilmente configurar el nombre del remitente para simular ser una entidad bancaria, una institución gubernamental o cualquier organización legítima. La combinación de números con prefijos internacionales creíbles y la posibilidad de personalizar el nombre del remitente crea el escenario perfecto para campañas de smishing (SMS phishing) altamente convincentes y difíciles de detectar para usuarios no técnicos.

## Investigación de Llamadas Suplantadas

La investigación se extendió hacia las funcionalidades de voz, donde se descubrieron capacidades aún más preocupantes. El sistema permite en ciertos escenarios configurar parámetros SIP y modificar el Caller ID, aunque no siempre funciona de manera consistente. En algunos casos específicos, es posible realizar llamadas desde números que teóricamente no deberían estar disponibles para el usuario, probablemente debido a fallos de configuración en las rutas SIP o inconsistencias en las validaciones del sistema.

Para demostrar este riesgo de manera controlada y ética, se utilizó el número de teléfono de un colaborador -con su consentimiento explícito y presencia física durante todas las pruebas- para realizar una llamada al dispositivo personal. El resultado fue contundente: el teléfono mostró el número del colaborador como remitente de la llamada, a pesar de que él no era quien realmente estaba realizando la llamada. Esta capacidad de suplantación de números conocidos o legítimos representa un riesgo extremadamente alto para ataques de vishing (voice phishing) y podría ser explotada para campañas de extorsión o ingeniería social avanzada.

## Escenarios de Ataque y Impacto Potencial

La gravedad de estas vulnerabilidadess no puede subestimarse. Un atacante con conocimientos técnicos moderados podría registrar una cuenta con datos falsos, obtener crédito de prueba de manera sencilla, y comenzar inmediatamente campañas de suplantación masiva. Las implicaciones de seguridad son enormes y abarcan múltiples escenarios de riesgo.

En el escenario de suplantación bancaria, un atacante podría enviar SMS masivos aparentando venir de entidades financieras legítimas, redirigiendo a las víctimas hacia sitios de phishing diseñados para robar credenciales de acceso. En el caso de extorsión telefónica, la capacidad de suplantar números oficiales de autoridades o empresas permitiría a los atacantes solicitar información personal confidencial o realizar demandas de pago bajo falsas pretensiones.

Otro escenario preocupante es el de campañas de desinformación, donde los atacantes podrían utilizar números legítimos para difundir mensajes fraudulentos, dañando la reputación de empresas y creando situaciones de caos social. La combinación de registros con datos falsos, obtención inmediata de crédito, capacidad de modificar el Caller ID y la ausencia de verificaciones rigurosas crea un ecosistema perfecto para el fraude telefónico organizado.

## Fundamentos Técnicos de las Vulnerabilidades

La posibilidad de realizar estas suplantaciones tiene sus raíces en deficiencias estructurales de los protocolos de voz sobre IP. Los protocolos VoIP como SIP y RTP fueron diseñados primordialmente para garantizar funcionalidad y compatibilidad, relegando aspectos de seguridad a un segundo plano. La suplantación es técnicamente posible debido a múltiples factores interconectados.

Entre estos factores destacan la falta de autenticación estricta en muchos carriers, que confían ciegamente en la información del Caller ID recibida; las configuraciones permisivas en routers SIP que no validan adecuadamente el origen real de las llamadas; la interconexión de redes con diferentes niveles de seguridad entre proveedores; y la necesidad de mantener compatibilidad retroactiva con sistemas legacy que carecen de mecanismos de seguridad modernos.

Además, la economía competitiva de los servicios VoIP lleva a muchos proveedores a priorizar la facilidad de uso y la accesibilidad sobre la seguridad. Esta dinámica de mercado resulta en prácticas como la minimización de fricción en el registro, la oferta de pruebas gratuitas inmediatas sin verificaciones robustas, y el mantenimiento de precios bajos mediante el recorte de controles de seguridad esenciales.

## Recomendaciones de Seguridad

Para los usuarios finales, esta investigación refuerza la necesidad crítica de mantener un escepticismo saludable hacia cualquier comunicación no solicitada, incluso cuando aparenta venir de números conocidos o entidades legítimas. Se recomienda encarecidamente no proporcionar información sensible por teléfono o mediante enlaces recibidos por SMS sin verificar previamente la autenticidad a través de canales alternativos oficiales.

Para los proveedores de servicios de telecomunicaciones, este estudio evidencia la urgente necesidad de implementar protocolos de autenticación más robustos y sistemas de verificación de identidad estrictos. Mecanismos como STIR/SHAKEN en Norteamérica representan pasos en la dirección correcta, pero su implementación global sigue siendo inconsistente y fragmentada.

Los desarrolladores de plataformas VoIP deben priorizar la implementación de autenticación multifactor, la validación estricta de datos de registro, auditorías regulares de configuraciones SIP y sistemas de monitorización proactiva para detectar intentos de spoofing. La seguridad debe integrarse desde el diseño inicial de los sistemas, no como una capa adicional posterior.

## Conclusión y Reflexiones Finales

Esta investigación demuestra de manera tangible cómo servicios legítimos de VoIP pueden ser weaponizados para fines maliciosos cuando no se implementan controles de seguridad adecuados. La facilidad con que se pueden eludir las medidas de verificación básicas y la potencia de las capacidades de suplantación disponibles representan una amenaza significativa para la seguridad de las comunicaciones telefónicas.

Lo más preocupante es que IllyVoIP no constituye un caso aislado. Existen numerosas plataformas similares en el mercado, muchas de ellas con controles de seguridad aún más laxos y funcionalidades potencialmente más peligrosas. El conocimiento de estas técnicas y vulnerabilidades es fundamental tanto para desarrollar mejores defensas como para educar al público general sobre los riesgos en el panorama moderno de las telecomunicaciones.

El compromiso ético ha sido fundamental throughout toda esta investigación, garantizando que todas las pruebas se realizaron con consentimiento explícito, en entornos controlados y sin afectación a terceros. Este enfoque responsable permite exponer importantes vulnerabilidades de seguridad mientras se mantienen los más altos estándares éticos en la investigación de ciberseguridad.

---

<div align="center">

**⚠️ AVISO LEGAL**: Esta investigación tiene fines exclusivamente educativos. El conocimiento aquí documentado debe utilizarse únicamente para fortalecer medidas de seguridad y protección. La reproducción de estas técnicas sin el consentimiento explícito de todas las partes involucradas es ilegal y éticamente reprobable.

**Última actualización**: Diciembre 2024

</div>
