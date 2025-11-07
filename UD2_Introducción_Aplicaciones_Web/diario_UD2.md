## Diario de Aprendizaje - UT2: Introducción a Aplicaciones Web

### Qué he aprendido

En esta unidad he entendido cómo está compuesto el ecosistema base de las aplicaciones web modernas.  
He comprendido cuál es el rol real de HTTP, Apache, los modelos de arquitecturas web (cliente-servidor, 2 capas, 3 capas) y la diferencia práctica entre servidores web y servidores de aplicaciones.

Además he aprendido conceptos básicos de virtualización y contenedores.  
He visto cómo VirtualBox permite levantar máquinas virtuales completas y cómo Docker permite lanzar servicios en contenedores ligeros para web y app server (Nginx / Tomcat). Ya empiezo a entender cómo esto se utiliza realmente en despliegues profesionales.

### Qué no entiendo

Aún me cuesta visualizar bien **la frontera exacta** entre servidor web y servidor de aplicaciones en proyectos reales grandes.  
También necesito interiorizar mejor cuándo una empresa usaría VM vs cuándo usaría contenedores.

### Qué es lo que más me ha gustado y qué es lo que menos

Lo que más me ha gustado ha sido ver Docker funcionando tan rápido y entender que puedo lanzar servicios completos sin instalaciones complejas.  
Me parece brutal para pruebas y despliegues rápidos.

Lo que menos me ha gustado ha sido la cantidad de términos nuevos en poco tiempo (HTTP, arquitecturas, Apache Linux/Windows, virtualización, SSH…). Requiere bastante cabeza ordenar estos conceptos.

### Qué más me gustaría aprender relacionado con la Unidad

Quiero profundizar en:

- despliegue real y automatización con contenedores (compose)
- cómo trabajan juntas varias capas dentro del CI/CD real
- cómo se protege correctamente un servidor web (HTTPS, certificados, firewalls, bastiones SSH, etc.)
- cómo se escala una app web para producción (balanceadores, alta disponibilidad)

Además me interesa ver ejemplos reales de arquitecturas modernas estilo microservicios.
