# Desenvolvemento con containers+vscode+laravel

Laravel é un práctico framework de PHP que pode ser usado para infinidade de aplicacións web -e de escritorio!-

Imos crear un entorno de traballo virtualizado grazas a Docker e WSL2. E empregaremos VSCode como editor de código e *director de orquestra* para construir unha pequena aplicación con Laravel.

## Iniciación en Windows

Antes de crear unha nova aplicación con Laravel na túa máquina Windows, imos a instalar [Docker Desktop](https://www.docker.com/products/docker-desktop). A continuación, asegúrate de que o subsistema de Windows para Linux 2 (WSL2) está instalado e activado. WSL permite executar binarios executables de Linux de forma nativa en Windows 10. Pódese atopar información sobre como instalar e activar WSL2 na [documentación do entorno para desenvolvedores de Microsoft](https://docs.microsoft.com/en-us/windows/wsl/install-win10). 

Despois de instalar e habilitar WSL2, asegurate de que Docker Desktop está configurado para usar o backend WSL2. 

Se todo funciona correctamente xa estás preparado para crear o teu primeiro proxecto Laravel. 

Inicia o [terminal de Windows](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=en-us&gl=US) e comeza unha nova sesión de terminal para o sistema operativo Linux que teñas en WSL2. A continuación, podes usar un comando de terminal simple para crear un novo proxecto Laravel. 

*Por exemplo, para crear unha nova aplicación Laravel nun directorio chamado "sample-app", podes executar na terminal o seguinte comando: 

```bash
   curl -s https://laravel.build/sample-app | bash
```







----

_\_ref:_

https://laravel.com/docs/9.x/installation#getting-started-on-windows

Using Laravel in VS Code (Start Quickly with a Dev Container! 📦)  &rarr; https://www.youtube.com/watch?v=ojWxCP1lT-Y

https://laravel-news.com/your-first-laravel-application