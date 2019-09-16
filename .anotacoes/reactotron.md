# Configurando o Reactotron

> O Reactotron é uma forma de fazer debug em uma aplicação ReactJS. Muito utilizado quando é usado Redux também.

Para começar usá-lo, baixe o app para desktop.

## Configurando seu projeto com o Reactotron

Para que seu projeto use o reactotron, baixe os pacotes:

```
yarn add reactotron-react-native
```

- Instalamos como dependência de produção porque iremos utilizá-lo no código, se fosse instalado como developer, o eslint iria reclamar.

- Para resolvermos esse problema, vamos configurar no projeto que o reactotron irá ser usado somente em desenvolvimento.

```js
// config/ReactotronConfig.js

import Reactotron from 'reactotron-react-native';

if (__DEV__) {
  const tron = Reactotron.configure()
    .useReactNative()
    .connect();

  console.tron = tron;

  tron.clear();
}
```

- Se o eslint reclamar da variável global __ DEV __ como não definida adicione ela no objeto globals do seu eslint:

```js
// .eslintrc.js

globals: {
  Atomics: 'readonly',
  SharedArrayBuffer: 'readonly',
  __DEV__: 'readonly',
},
```

Por fim, para ver se está funcionando:

```js
import React from 'react';
import { View, Text } from 'react-native';

import './config/ReactotronConfig';

console.tron.log('Ola kassio');

export default function App() {
  return (
    <View>
      <Text>Olá, Kássio</Text>
    </View>
  );
}
```

- Se por acaso você estiver no emulador ou usb com android e não aparecer nada no app do reactron, execute o seguinte passo no adb:

```
adb reverse tcp:9090 tcp:9090
```

- Aqui estamos trocando a porta metro bundle para o reactotron funcionanar.
