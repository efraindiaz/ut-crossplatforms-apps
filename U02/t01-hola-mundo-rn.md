# T01 Hola Mundo React Native

📎 ***React Native Roadmap*: https://roadmap.sh/react-native
## Expo

Requerimientos:
- [Node.js (LTS)](https://nodejs.org/en/).
- macOS, Windows (Powershell and [WSL 2](https://expo.fyi/wsl)), and Linux are supported.

Crear una aplicación usando Expo

`create-expo-app`

```bash
npx create-expo-app@latest
```

`--template` creando un proyecto en blanco con lo mínimo

```bash
npx create-expo-app@latest --template blank
```

Correr una aplicación de RN con `expo`

```shell
npx expo start
```

Limpiar cache de npm

```shell
npm cache clean --force
```


##  🌐 Tunneling

 Conectarse a un servidor de desarrollo a través de una URL proxy, `npx expo start` proporciona soporte integrado para tunelización a través de `ngrok`.

Para habilitar la tunelización, primero instalamos `@expo/ngrok`:

```shell
npm install -g @expo/ngrok
```

A continuación, ejecutamos lo siguiente para iniciar el servidor de desarrollo desde una URL de túnel:

```shell
npx expo start --tunnel
```

## 🚀 React Native Core Components

Componentes básicos para crear una interfaz de usuario. No dependen de una plataforma específica, lo que les permite operar en dispositivos iOS y Android por igual.
### Componentes básicos

- `View`
- `Text`
- `TextInput`
- `Button`
- `FlatList`

🖥️ **Ejemplo**:

```jsx
import { View, Text } from 'react-native';

export default function CoreComponentsExample() {
  return (
    <View>
      <Text>¡Hola desde un Core Component!</Text>
    </View>
  );
}
```

## 🚀 React Native Components

Componentes construidos utilizando Core Components como base. Estos componentes pueden ser:

- **Componentes personalizados**
- **Componentes de terceros**

✅ **Características**:

- Extienden la funcionalidad de los Core Components.
- Pueden provenir de bibliotecas externas o ser creados manualmente.

📦 **Ejemplo**:

- `react-native-paper` → UI lista para usar.

Custom Component: 

```jsx
import { View, Text, StyleSheet } from 'react-native';

export default function CustomCard ({ title, description }){
  return (
    <View style={styles.card}>
      <Text style={styles.title}>{title}</Text>
      <Text style={styles.description}>{description}</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  card: {
    backgroundColor: '#fff',
    padding: 20,
    margin: 10,
    borderRadius: 10,
    elevation: 5,
  },
  title: {
    fontWeight: 'bold',
    fontSize: 18,
  },
  description: {
    color: '#666',
    marginTop: 5,
  },
});
```


##  ⚛ Fundamentos de React

React Native se ejecuta sobre React. Para sacar el máximo provecho de React Native, es útil entender React en sí.

Conceptos básicos detrás de React:

- Components
- JSX
- Props
- State

**⚛ Components**

```jsx
import {Text} from 'react-native';

export default function Cat(){
  return <Text>Hola, Soy un michi 😽!</Text>;
};
```

**⚛ JSX + Props**

**_JSX_** es una extensión de sintaxis para JavaScript que permite escribir marcado similar a HTML dentro de una archivo JavaScript:

```jsx
<Text>Miau</Text>
```

Los **_Props_** te permiten personalizar los componentes de React. Por ejemplo, aquí pasamos a cada componente `<Cat>` un nombre diferente para que `Cat` lo renderice:

```jsx
import { Text } from 'react-native';

export default function Cat({name}){
	return <Text>Hola, Soy el michi: {name} 😽!</Text>;
};
```

**⚛ State**

El estado es útil para manejar datos que cambian con el tiempo o que provienen de la interacción del `usuario`. 

```jsx
import {useState} from 'react';
import {View, Button, Text} from 'react-native';

export default function Cat({name}){
	const [isHungry, setIsHungry] = useState(true);
	return (
		<View>
			<Text>Hola, Soy el michi: {name} 😽!</Text>
			<Button
		        onPress={() => {
		          setIsHungry(false);
		        }}
		        disabled={!isHungry}
		        title={isHungry ? 'Dame comidaaa!' : 'Gracias!'}
		    />
		</View>
	);
};
```

---
### 🧠 Actividad: Listas en React Native

Investigar y comprender cómo funcionan las listas en React Native, especialmente los componentes `FlatList` y `SectionList`, y aplicarlos al ejercicio actual.

```jsx
//Una interfaz de alto rendimiento para la representación de listas. 
<FlatList /> 
```

---







