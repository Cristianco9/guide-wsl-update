# IENSC
# Actualización y Configuración de PowerShell 7 y WSL 2 en Equipos con Windows 11

Este documento tiene como propósito guiar paso a paso a las personas encargadas 
de la actualización e instalación de **PowerShell 7**, la configuración de **WSL 2** 
como backend predeterminado, y el establecimiento de **Ubuntu** como distribución
 principal en cada uno de los equipos de las aulas **STEAM**.

> ⚠️ **Requisitos previos**: 
Todos los equipos deben tener acceso a internet y privilegios de administrador.
---

## 1. Actualizar PowerShell a la versión 7

### Paso 1.1 - Descargar PowerShell 7

1. Ingresar al sitio oficial:
   https://github.com/PowerShell/PowerShell/releases
2. Descargar el archivo `.msi` correspondiente a Windows x64 (ejemplo: `PowerShell-7.x.x-win-x64.msi`).
---


### Paso 1.2 - Instalar PowerShell 7

1. Ejecutar el `.msi` como administrador.
2. Seguir el asistente de instalación.
3. Asegurarse de marcar las siguientes opciones:
   - **Add to PATH**
   - **Register Windows Event Logging**
   - **Enable PowerShell remoting**
---

### Paso 1.3 - Verificar la instalación

Abrir una terminal PowerShell y ejecutar:

```powershell
pwsh
```

Dentro de PowerShell 7, verificar la versión:

```powershell
$PSVersionTable
```
---

### Paso 1.4 - Cambiar PowerShell predeterminado en Terminal de Windows:

1. Abre **Terminal de Windows**.
2. Haz clic en la flecha hacia abajo (`˅`) al lado de la pestaña `+` y selecciona **Configuración**.
3. En el panel izquierdo, selecciona **Inicio > Perfil predeterminado**.
4. Cambia a **PowerShell 7**.
5. Haz clic en **Guardar**.

> Esto hará que cada vez que abras **Windows Terminal**, inicie con **PowerShell 7** en lugar de **PowerShell 5.1** o **CMD**.
---

## 2. Actualizar y configurar WSL 2

### Paso 2.1 - Actualizar WSL a WSL 2

Ejecutar en PowerShell 7 con permisos de administrador

Actualizar WSL:

```powershell
wsl --update
```

Configurar WSL 2 con distribución por defecto:

```powershell
wsl --set-default-version 2
```

>  **Nota**: 
Es posible que se deba reiniciar el equipo después de este paso.
---

### Paso 2.2 - Verificar versión instalada

ejecutar en PowerShell 7:

```powershell
wsl --status
```

Debe aparecer algo como:

```powershell
Default Version: 2
```
---

## 3. Configurar Ubuntu como distribución predeterminada

### Paso 3.1 -  Establecer Ubuntu como distribución predeterminada

ejecutar en PowerShell 7:

```powershell
wsl --set-default Ubuntu
```

Verificar:

```powershell
wsl -l -v
```

>  **Observación**: 
Debe aparecer Ubuntu con un `*` indicando que es la distribución por defecto.
---

## 4. Verificación final

### Paso 4.1 - Probar la ejecución de WSL 2:

* Abrir PowerShell 7 y ejecutar:

```powershell
wsl
```
Esto debería abrir Ubuntu en modo terminal.
---

### Paso 4.2 - Confirmar que el Kernel WSL 2 este en uso:

```powershell
wsl --list --verbose
```

El campo VERSION debe decir 2.

---

## 5. Recomendaciones

- Realizar pruebas en un equipo antes de proceder con la instalación masiva.
- Documentar cualquier error encontrado durante la instalación.
- Mantener un registro por equipo de los pasos realizados y resultados (puede usarse Excel).
- Verificar que después de la instalación se puede ejecutar `npm`, `node`, y `git` dentro de Ubuntu.
---

## 6. Recursos adicionales

- [Documentación oficial de PowerShell](https://learn.microsoft.com/en-us/powershell/)
- [Documentación de WSL](https://learn.microsoft.com/en-us/windows/wsl/)
- [Instalación de WSL 2 paso a paso](https://learn.microsoft.com/en-us/windows/wsl/)
---

## 7. Contacto

En caso de dudas o bloqueos técnicos, contactar con el ingeniero responsable del aula STEAM.