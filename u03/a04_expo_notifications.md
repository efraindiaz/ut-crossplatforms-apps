### ✨ Actividad: Integración de Expo Notifications ✨

#### 🛠️ Requisitos previos:
- Haber trabajado con el proyecto de autenticación en actividades pasadas.
- Contar con una cuenta de Expo.
- Tener instalado EAS CLI.
- Tener configurada la API base disponible en el siguiente repositorio:
  - [Demo API](https://github.com/efraindiaz/demo-api)
  - [Auth App con Expo Notifications](https://github.com/efraindiaz/auth_app_bc)

---

## 💻 Configuración de la API

1. **Agregar un archivo `.env`** con las siguientes variables de entorno:
   ```plaintext
   PORT=3000  # O el puerto que desees usar
   JWT_SECRET=tu_secreto_jwt
   ```
2. **Instalar y configurar NGROK**:
   - Descarga e instala NGROK desde [https://ngrok.com/download](https://ngrok.com/download).
   - Inicia sesión en el dashboard de NGROK y genera un dominio estático.
   - Usa este dominio en la configuración de la API para que pueda ser accesible desde la aplicación móvil.
3. **Crear un nuevo endpoint para enviar notificaciones con la API de Expo**:
   - Implementar el middleware `verifyToken` para validar el token enviado en el header `Authorization`.
   - Usar la API de Expo para enviar notificaciones push.

---

## 🌟 Configuración del proyecto Expo

### 1️⃣ Instalar EAS CLI
EAS CLI es necesario para interactuar con los servicios de Expo:
```bash
npm install -g eas-cli
```

### 2️⃣ Iniciar sesión en Expo
Si no has iniciado sesión:
```bash
eas login
```

### 3️⃣ Configurar el proyecto para EAS Build
Ejecuta el siguiente comando para configurar el proyecto:
```bash
eas build:configure
```
Este proceso generará el `Project ID`, necesario para obtener el **Expo Push Token**.

---

## 📲 Desarrollo de la aplicación

### 🔐 Autenticación
- Implementar el inicio de sesión utilizando la API.

### 🛡️ Configuración de AXIOS
- Implementar `AXIOS` junto con los `interceptors` para manejar las peticiones (excepto el login).

### 🗃 Implementación de Tabs
- Agregar navegación con **TABS** para diferenciar las notificaciones:
  - **Tab 1:** Notificaciones locales.
  - **Tab 2:** Push notifications.

### 📢 Implementación de Expo Notifications
- Ajustar la lógica para que las **Push Notifications** sean enviadas desde la API en lugar de directamente desde el dispositivo.
- Enviar el **Expo Push Token** a la API para que esta pueda gestionar el envío de notificaciones.
- Cambiar la información de la notificación de ejemplo y añadirle algun diferenciador. 

---

- 🔗 **Documentación Expo Notifications**: [Expo Notifications](https://docs.expo.dev/build/setup/)

