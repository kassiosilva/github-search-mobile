# ESLint, Prettier e EditorConfig

> Antes de tudo, delete o arquivo .eslintrc.js do seu projeto e verifique se o eslint já está instalado, caso esteja remova ele da suas dependências. O prettier também.

## Configurando o EditorConfig

Com a extensão editorconfig do vscode, crie o arquivo na raiz do seu projeto adicione as seguintes informações:

```
root = true

[*]
end_of_line = lf
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

## Configurando o ESLint

1. Instale o eslint com o comando:

```
yarn add eslint -D
```

2. Execute o comando para configura o eslint no seu projeto:

```
yarn eslint --init
```

Após isso, irá ser criado um arquivo .eslintrc.js na raiz do seu projeto.

3. Instale mais algumas dependências complementares do eslint:

```
yarn add prettier eslint-config-prettier eslint-plugin-prettier babel-eslint -D
```

### .eslintrc.js

Vamos fazer algumas configurações nesse arquivo.

```js
module.exports = {
  env: {
    es6: true,
  },
  extends: [
    'airbnb',
    'prettier',
    'prettier/react'
  ],
  globals: {
    Atomics: 'readonly',
    SharedArrayBuffer: 'readonly',
  },
  parser: 'babel-eslint',
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 2018,
    sourceType: 'module',
  },
  plugins: [
    'react',
    'prettier'
  ],
  rules: {
    'prettier/prettier': 'error',
    'react/jsx-filename-extension': [
      'warn',
      { extensions: ['.jsx', '.js'] }
    ],
    'import/prefer-default-export': 'off'
  },
};
```

Feito isso, vamos agora criar e configurar o arquivo **.prettierrc**:

```
{
  "singleQuote": true,
  "trailingComma": "es5"
}
```

Agora o eslint está devidamente configurado!




