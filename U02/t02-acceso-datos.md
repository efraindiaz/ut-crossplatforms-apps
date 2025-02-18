# T02 - Acceso a datos

Para realizar solicitudes HTTP en React Native se utiliza la función `fetch`.

---
## 1️⃣ Elementos Básicos

- **fetch**: Función nativa de JavaScript que permite realizar solicitudes HTTP de manera sencilla.
- **useEffect**: Hook de React que permite ejecutar efectos secundarios, como llamadas a una API.
- **useState**: Hook para manejar el estado local del componente.

## 2️⃣  Ejemplo

```jsx
import { useEffect, useState } from 'react';
import { Text, View } from 'react-native';

// Componente principal de la aplicación
const App = () => {
	// Definición de estados para almacenar los datos
	const [data, setData] = useState([]);

	// useEffect para hacer la llamada a la API al cargar el componente
	useEffect(() => {
		// fetch: API nativa de JavaScript para hacer solicitudes HTTP
		fetch('https://jsonplaceholder.typicode.com/posts')
		.then(res => res.json())
		.then(setData)
	}, []);

  // Renderizamos la lista de publicaciones una vez que los datos están disponibles
  return (
    <View>
      <FlatList />
    </View>
  );
};

export default App;
```

---
