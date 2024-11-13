# Introdução ao React

## 1. O que é React?

React é uma biblioteca JavaScript desenvolvida pelo Facebook para criar interfaces de usuário interativas, especialmente em aplicações de página única. Ele facilita a criação de componentes reutilizáveis e gerencia a atualização de dados com eficiência.

## 2. Conceitos Fundamentais

### 2.1. Componentes

Componentes são blocos básicos de construção de interfaces React. Existem dois tipos principais:
- **Componentes Funcionais**: Definidos como funções JavaScript.
- **Componentes de Classe**: Definidos como classes que herdam de `React.Component` (mais utilizados em versões antigas do React).

#### Exemplo de Componente Funcional

```javascript
import React from 'react';

function BemVindo() {
  return <h1>Bem-vindo ao React!</h1>;
}

export default BemVindo;
```
### 2.2. JSX
JSX é uma extensão de sintaxe para JavaScript que permite escrever HTML dentro de JavaScript. Ele simplifica a criação da estrutura de componentes.

#### Exemplo de JSX

```javascript
const element = <h1>Olá, mundo!</h1>;
```

### 2.3. Props
Props (propriedades) são parâmetros passados para componentes, permitindo a passagem de dados de um componente pai para um componente filho.

#### Exemplo de Uso de Props

```javascript function Saudacao(props) {
  return <h1>Olá, {props.nome}!</h1>;
}

<Saudacao nome="Érica" />;
```

## 2.4. Estado (State)
O estado permite que os componentes tenham dados que possam ser alterados com o tempo. Usamos o useState para gerenciar o estado em componentes funcionais.

Exemplo de Componente com Estado

```javascript import React, { useState } from 'react';

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Você clicou {contador} vezes</p>
      <button onClick={() => setContador(contador + 1)}>Clique aqui</button>
    </div>
  );
}
```

## 2.5. Eventos
React facilita o trabalho com eventos HTML, como onClick, onChange, e onSubmit, que podem ser atribuídos diretamente a elementos.

#### Exemplo de Evento

```javascript function EventoClique() {
  function handleClick() {
    alert('Botão clicado!');
  }

  return <button onClick={handleClick}>Clique aqui</button>;
}
```

# 3. Hooks
Hooks são funções que permitem o uso de estado e outros recursos do React em componentes funcionais.

## 3.1. Principais Hooks
useState: Gerencia o estado local em um componente funcional.
useEffect: Executa efeitos colaterais, como chamadas de API, após o componente ser renderizado.

#### Exemplo do useEffect

```javascript import React, { useState, useEffect } from 'react';

function ExemploAPI() {
  const [dados, setDados] = useState([]);

  useEffect(() => {
    fetch('https://api.exemplo.com/dados')
      .then(response => response.json())
      .then(data => setDados(data));
  }, []); // Executa apenas uma vez

  return (
    <ul>
      {dados.map(item => (
        <li key={item.id}>{item.nome}</li>
      ))}
    </ul>
  );
}
```

# 4. Estrutura Básica de um Projeto React

Ao criar um projeto React com create-react-app, você terá a seguinte estrutura:

## Estrutura de Pastas do Projeto


## Estrutura de Pastas do Projeto

```plaintext
my-app/
├── src/
│   ├── App.js          // Componente principal da aplicação
│   ├── index.js        // Ponto de entrada da aplicação
│   ├── components/     // Componentes reutilizáveis
│   └── ...
├── public/
│   └── index.html      // HTML principal
└── package.json        // Dependências e scripts
```

# 5. Ciclo de Vida dos Componentes
Com o uso de hooks, o ciclo de vida de componentes é gerenciado com useEffect:

Montagem: Inicialização do componente.
Atualização: Quando o estado ou props mudam.
Desmontagem: Limpeza após o componente ser removido.

# 6. Trabalhando com APIs
React facilita a integração com APIs para buscar dados externos. O hook useEffect é geralmente usado para realizar chamadas de API.

#### Exemplo de Chamada de API

```javascript import React, { useState, useEffect } from 'react';

function ListaDeUsuarios() {
  const [usuarios, setUsuarios] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(data => setUsuarios(data));
  }, []);

  return (
    <ul>
      {usuarios.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```
