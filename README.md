# WinBox DEB

Paquete `.deb` para instalar **MikroTik WinBox en Kubuntu y otras distribuciones basadas en Debian/Ubuntu**, utilizando Wine para ejecutar el binario oficial de WinBox.

## Características

* Instalación mediante paquete `.deb`
* Integración con el menú de aplicaciones de KDE Plasma
* Icono de WinBox
* Ejecución mediante Wine
* Compatible con Kubuntu y sistemas basados en Debian/Ubuntu
* Instalación sencilla mediante APT o `dpkg`
* Desinstalación mediante el gestor de paquetes

## Requisitos

El sistema debe contar con una distribución basada en Debian o Ubuntu.

Wine es utilizado para ejecutar el archivo `winbox64.exe`.

## Instalación

Descarga el archivo:

```text
winbox-deb.deb
```

desde la sección **Releases** de este repositorio.

Instálalo con:

```bash
sudo apt install ./winbox-deb.deb
```

También puedes instalarlo mediante `dpkg`:

```bash
sudo dpkg -i winbox-deb.deb
sudo apt install -f
```

Una vez instalado, busca **WinBox** en el menú de aplicaciones de Kubuntu.

## Ejecución

El ejecutable se instala en:

```text
/opt/winbox/winbox64.exe
```

El acceso directo se registra en:

```text
/usr/share/applications/winbox.desktop
```

También es posible ejecutarlo manualmente desde una terminal:

```bash
wine /opt/winbox/winbox64.exe
```

## Estructura del paquete

```text
winbox-deb/
├── DEBIAN/
│   └── control
│
├── opt/
│   └── winbox/
│       └── winbox64.exe
│
└── usr/
    └── share/
        ├── applications/
        │   └── winbox.desktop
        │
        └── icons/
            └── hicolor/
                └── 256x256/
                    └── apps/
                        └── winbox.png
```

## Archivo de control

El archivo:

```text
winbox-deb/DEBIAN/control
```

contiene la información del paquete.

Ejemplo:

```text
Package: winbox
Version: 1.0.0
Section: net
Priority: optional
Architecture: all
Depends: wine
Maintainer: Israel Rivas Iglesias
Description: MikroTik WinBox for Kubuntu
 WinBox packaged for Kubuntu and Debian based systems.
```

> El nombre del archivo `winbox-deb.deb` puede ser diferente al nombre interno definido en `Package:`.

## Construcción del paquete

Para construir el paquete, ejecuta:

```bash
dpkg-deb --build winbox-deb
```

Esto generará el archivo:

```text
winbox-deb.deb
```

## Verificar información del paquete

Puedes consultar la información interna del paquete con:

```bash
dpkg-deb -I winbox-deb.deb
```

También puedes consultar los archivos que contiene:

```bash
dpkg-deb -c winbox-deb.deb
```

## Desinstalación

El comando de desinstalación depende del nombre definido en el campo `Package:` del archivo `control`.

Por ejemplo, si el archivo contiene:

```text
Package: winbox
```

puedes desinstalarlo con:

```bash
sudo apt remove winbox
```

Para eliminarlo junto con sus archivos de configuración:

```bash
sudo apt purge winbox
```

## Licencia y marcas

WinBox es software desarrollado por MikroTik.

Este proyecto no está afiliado, patrocinado ni oficialmente respaldado por MikroTik.

El objetivo de este repositorio es proporcionar un paquete `.deb` para facilitar la instalación e integración de WinBox en sistemas Linux compatibles, utilizando Wine.

Los nombres, marcas y logotipos de MikroTik pertenecen a sus respectivos propietarios.

## Autor

**Israel Rivas Iglesias**

## Estado del proyecto

Proyecto en desarrollo.

### Próximas mejoras

* [ ] Script automático para generar el paquete
* [ ] Actualización sencilla de la versión de WinBox
* [ ] Repositorio APT
* [ ] Firma GPG del paquete
* [ ] Mejor integración con KDE Plasma
* [ ] Compatibilidad ampliada con Ubuntu y Debian
