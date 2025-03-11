# 🚀 Expo Sensors

La biblioteca `expo-sensors` de Expo proporciona acceso a diversos sensores del dispositivo en aplicaciones desarrolladas con React Native. Estos sensores permiten medir aspectos como movimiento, orientación, presión, campos magnéticos, luz ambiental y conteo de pasos.

## 📡 Sensores disponibles en `expo-sensors`

### 📌 Acelerómetro (`Accelerometer`)

Mide la aceleración del dispositivo en las tres dimensiones del espacio, detectando movimientos o vibraciones.

### 🌡️ Barómetro (`Barometer`)

Mide la presión atmosférica, útil para aplicaciones que requieren información sobre altitud o condiciones climáticas.

### 🔄 Giroscopio (`Gyroscope`)

Mide la rotación del dispositivo en el espacio, proporcionando datos sobre la orientación y movimientos angulares.

### 🧭 Magnetómetro (`Magnetometer`)

Detecta campos magnéticos, lo que permite, por ejemplo, implementar una brújula digital.

### 💡 Sensor de luz (`LightSensor`)

Mide la luz ambiental, permitiendo ajustar el brillo de la pantalla o adaptar la interfaz de usuario según las condiciones de iluminación.

### 🚶‍♂️ Podómetro (`Pedometer`)

Cuenta el número de pasos dados por el usuario, útil para aplicaciones de seguimiento de actividad física.

### 📱 Movimiento del dispositivo (`DeviceMotion`)

Combina datos de varios sensores para proporcionar información detallada sobre el movimiento y la orientación del dispositivo.

## 🚀 Instalación de `expo-sensors`

Para utilizar estos sensores en tu proyecto de React Native con Expo, primero instala la biblioteca:

```bash
npx expo install expo-sensors
```

## 🛠️ Uso de los sensores

A continuación, un ejemplo de cómo usar el **acelerómetro**:

```javascript
import { Accelerometer } from 'expo-sensors';

Accelerometer.addListener(({ x, y, z }) => {
  console.log(`Aceleración en X: ${x}, Y: ${y}, Z: ${z}`);
});
```

## ⚠️ Consideraciones importantes

- 📌 **Optimización del rendimiento**: Maneja adecuadamente las suscripciones a los sensores para evitar un uso innecesario de batería.
- 🔐 **Permisos**: Algunos sensores requieren permisos adicionales, revisa la documentación oficial de Expo.

Para más información y ejemplos detallados, consulta la documentación oficial de Expo sobre `expo-sensors`: [Expo Sensors Docs](https://docs.expo.dev/versions/latest/sdk/sensors/) 📖.
