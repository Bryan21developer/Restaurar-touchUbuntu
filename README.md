# 🛠️ Solución para Touchpad Synaptics no detectado en Ubuntu (Toshiba Satellite)

Este documento describe cómo activar el parámetro `psmouse.synaptics_intertouch=1` en Ubuntu para mejorar la compatibilidad del touchpad Synaptics, especialmente en laptops Toshiba Satellite como el modelo S40-A.

## ✅ Problema

El touchpad funciona en Windows pero no responde en Ubuntu, aunque el sistema lo detecta. Esto puede deberse a que el kernel necesita un parámetro adicional para manejar correctamente el bus de comunicación del touchpad.

## 🧪 Solución: Activar `psmouse.synaptics_intertouch=1`

### 1. Abrir el archivo de configuración del GRUB

bash
```
sudo nano /etc/default/grub
```
2. Editar la línea de opciones del kernel
Busca esta línea: ```GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"```
Y cámbiala por esta:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash psmouse.synaptics_intertouch=1"
```

4. Actualizar la configuración del GRUB
 ```
sudo update-grub
```
5. Reiniciar el sistema
```
sudo reboot
```
🔍 Verificación
Después del reinicio, puedes verificar que el parámetro esté activo con:


🔄 Cambiar de sesión a Xorg (si estás usando Wayland)
Algunas herramientas como xinput no funcionan correctamente bajo Wayland. Para cambiar a Xorg:

Cierra sesión desde el menú de usuario.

En la pantalla de inicio de sesión, haz clic en el ícono de engranaje (⚙️) en la esquina inferior derecha.

Selecciona Ubuntu en Xorg.

Inicia sesión normalmente.
cat /proc/cmdline

También puedes comprobar que el touchpad esté habilitado con:
```
xinput list
xinput list-props "SynPS/2 Synaptics TouchPad"
```
