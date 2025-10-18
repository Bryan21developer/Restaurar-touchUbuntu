# 🛠️ Solución para Touchpad Synaptics no detectado en Ubuntu (Toshiba Satellite)

Este documento describe cómo activar el parámetro `psmouse.synaptics_intertouch=1` en Ubuntu para mejorar la compatibilidad del touchpad Synaptics, especialmente en laptops Toshiba Satellite como el modelo S40-A.

## ✅ Problema

El touchpad funciona en Windows pero no responde en Ubuntu, aunque el sistema lo detecta. Esto puede deberse a que el kernel necesita un parámetro adicional para manejar correctamente el bus de comunicación del touchpad.

## 🧪 Solución: Activar `psmouse.synaptics_intertouch=1`

### 1. Abrir el archivo de configuración del GRUB

```bash2. Editar la línea de opciones del kernel
Busca esta línea:

text
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Y cámbiala por esta:

text
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash psmouse.synaptics_intertouch=1"
3. Guardar y cerrar el archivo
Presiona Ctrl + O para guardar.

Presiona Enter para confirmar.

Presiona Ctrl + X para salir del editor.

4. Actualizar la configuración del GRUB
bash
sudo update-grub
5. Reiniciar el sistema
bash
sudo reboot
🔍 Verificación
Después del reinicio, puedes verificar que el parámetro esté activo con:

bash
cat /proc/cmdline
También puedes comprobar que el touchpad esté habilitado con:

bash
xinput list
xinput list-props "SynPS/2 Synaptics TouchPad"
💡 Notas adicionales
Este método ha sido probado en Ubuntu 22.04 y 24.04 con laptops Toshiba Satellite S40-A.

Si el touchpad sigue sin funcionar, considera probar una distribución como Linux Mint o Fedora, que a veces tienen mejor soporte para hardware específico.

Puedes instalar herramientas como gnome-tweaks para configurar gestos, clics y desplazamiento:

bash
sudo apt install gnome-tweaks
sudo nano /etc/default/grub
