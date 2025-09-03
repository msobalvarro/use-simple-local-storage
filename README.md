# use-simple-local-storage

Un hook de React ligero para manejar valores en `localStorage` de manera sencilla y tipada.

## Instalación

```bash
npm install use-simple-local-storage
# o
yarn add use-simple-local-storage
# o
pnpm add use-simple-local-storage
# o
bun install use-simple-local-storage
```

## Uso

```jsx
import { useSimpleLocalStorage } from "use-simple-local-storage";

function App() {
  const [name, setName] = useSimpleLocalStorage < string > "username";

  return (
    <div>
      <p>Nombre guardado: {name}</p>
      <input
        type="text"
        value={name ?? ""}
        onChange={(e) => setName(e.target.value)}
      />
    </div>
  );
}
```

## API

```jsx
useSimpleLocalStorage<T>(key: string): [T | null, (val: T) => void]
```

- `key`: clave bajo la que se almacenará el valor en `localStorage`.

- `T`: tipo del valor a guardar (ejemplo: `string`, `number`, `User`, etc).

## Ejemplos

Guardar un número

```JSX
const [count, setCount] = useSimpleLocalStorage<number>('counter')

```

Guardar un objeto

```JSX
type User = {
  id: number
  name: string
}

const [user, setUser] = useSimpleLocalStorage<User>('user')

```


## Consideraciones
- Este hook solo funciona en entornos con `localStorage` disponible (navegadores).
- Los valores se serializan con `JSON.stringify` y se parsean con `JSON.parse`.
- Si guardas valores complejos, asegúrate de que sean serializables


---
#### MIT © 2025 Merling Samuel Sobalvarro Reyes