### ¿Problemas con procesadores?

- **Problemas comunes al instalar Docker en procesadores antiguos** Algunos usuarios pueden experimentar problemas al instalar Docker en máquinas con procesadores **AMD** o **Intel** antiguos, ya que Docker depende de la virtualización para funcionar. Es importante verificar que tu procesador tenga **soporte para virtualización** (VT-x en Intel o AMD-V en AMD) y que esté habilitado en la BIOS.

      En equipos Windows, asegúrate de que Hyper-V esté activado, ya que Docker Desktop utiliza esta tecnología para crear contenedores.

      En macOS, Docker utiliza el **Apple Hypervisor Framework**.

- **Considera la arquitectura de tu procesador** Las arquitecturas `amd64` y `arm64` se refieren a diferentes conjuntos de instrucciones que los procesadores utilizan para ejecutar programas.

      amd64 (x86-64): Desarrollada por AMD, pero basada en la arquitectura x86 de Intel. Es la más común en PCs y servidores.

      arm64 (ARMv8-A o AArch64): Desarrollada por ARM Holdings, se utiliza en dispositivos móviles y servidores. Es más eficiente y multinúcleo. Es popular en dispositivos como Raspberry Pi Apple M1/M2, y en la nube con AWS Graviton.

      Las imágenes de Docker se crean y optimizan para una arquitectura específica. Esto significa que una imagen creada para amd64 (procesadores Intel y AMD de 64 bits) no se puede ejecutar de forma nativa en arm64 (procesadores ARM).  Comando para construir una imagen multiarquitectura:

      docker buildx build --platform linux/amd64,linux/arm64 -t mi-imagen:latest .**

- **Si falla el WSL, hacer la instalación offline siguiendo los pasos aquí:
https://learn.microsoft.com/en-us/windows/wsl/install**

-**Paso a paso:**

- Descargar desde este link https://github.com/microsoft/wsl/releases el ejecutable desde assets, el seleccionado en la captura de pantalla de aquí abajo:

<img width="970" height="349" alt="Captura de pantalla 2025-09-10 a las 12 28 25" src="https://github.com/user-attachments/assets/68f1ca27-4ad4-441e-8512-2a6d3dac660c" />

- Una vez descargado y ejecutado, pon este comando en terminal (powershell admin):
```bash
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```



🚨 🚨 ¿Entendéis lo que necesitamos? ¿Entendís el problema de la arquitectura de tu procesador? 🚨 🚨
