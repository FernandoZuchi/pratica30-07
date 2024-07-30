# Projeto 1 - Tela de Login e Cadastro 

Este projeto é uma aplicação React que implementa uma interface de login e cadastro. Abaixo estão os detalhes da configuração inicial e da estrutura dos arquivos.

## Estrutura do Projeto

- `App.js`
- `LoginSignup.jsx`
- `LoginSignup.css`
- `assets/` (contém imagens usadas no formulário)

## 1. Configuração do Arquivo `App.js`

O arquivo `App.js` é o ponto de entrada da aplicação e contém o componente principal que renderiza o componente `LoginSignup`.

```jsx
// Importa o componente LoginSignup, que será usado na aplicação principal
import LoginSignup from "./Components/LoginSignup/LoginSignup";

// Componente principal da aplicação
const App = () => {
  return (
    <div>
      {/* Renderiza o componente LoginSignup */}
      <LoginSignup />
    </div>
  )
}

// Exporta o componente App para uso em outras partes da aplicação
export default App;
```

## 2. Estilos Globais

Os estilos globais são definidos para garantir que o corpo da página ocupe toda a altura da viewport e tenha um fundo com gradiente.

### Arquivo `index.css` (ou equivalente)

```css
/* Define o estilo para o corpo da página */
body {
    margin: 0; /* Remove a margem padrão do body */
    height: 100vh; /* Define a altura da viewport para 100% da altura da tela */
    background: linear-gradient(#2A00B7, #42006C); /* Define um gradiente de fundo */
}
```

## 3. Componente `LoginSignup`

O componente `LoginSignup` gerencia a exibição dos campos de login e cadastro, alternando entre eles conforme o estado `action`.

### Arquivo `LoginSignup.jsx`

```jsx
// Importa os estilos do componente
import './LoginSignup.css';

// Importa as imagens usadas nos campos de entrada
import email from '../assets/email.png';
import password from '../assets/password.png';
import person from '../assets/person.png';

// Importa o hook useState do React para gerenciar o estado do componente
import { useState } from 'react';

// Componente de login e cadastro
const LoginSignup = () => {
    // Define o estado inicial do componente, que será "Cadastre-se"
    const [action, setAction] = useState("Cadastre-se");

    return (
        <div className='container'>
            {/* Seção do cabeçalho que exibe o título e uma linha embaixo */}
            <div className="header">
                <div className="text">{action}</div>
                <div className="underline"></div>
            </div>
            {/* Seção dos campos de entrada */}
            <div className="inputs">
                {/* Renderiza o campo de nome somente se a ação não for "Login" */}
                {action === "Login" ? <div></div> : <div className="input">
                    <img src={person} alt="" />
                    <input type="text" placeholder='Nome' />
                </div>}
                <div className="input">
                    <img src={email} alt="" />
                    <input type="email" placeholder='E-mail' />
                </div>
                <div className="input">
                    <img src={password} alt="" />
                    <input type="password" placeholder='Senha' />
                </div>
            </div>
            {/* Renderiza a mensagem "Esqueceu a senha?" somente se a ação for "Login" */}
            {action === "Cadastre-se" ? <div></div> : <div className="forgot-password">Esqueceu a senha? <span>Clique aqui!</span></div>}
            {/* Seção dos botões de ação */}
            <div className="submit-container">
                {/* Botão de "Cadastre-se" */}
                <div className={action === "Login" ? "submit gray" : "submit"} onClick={() => setAction("Cadastre-se")}>
                    Cadastre-se
                </div>
                {/* Botão de "Login" */}
                <div className={action === "Cadastre-se" ? "submit gray" : "submit"} onClick={() => setAction("Login")}>
                    Login
                </div>
            </div>
        </div>
    )
}

// Exporta o componente LoginSignup para uso em outras partes da aplicação
export default LoginSignup;
```

### Arquivo `LoginSignup.css`

```css
/* Estilo do contêiner principal do componente */
.container {
    display: flex;
    flex-direction: column; /* Alinha os itens verticalmente */
    margin: auto; /* Centraliza o contêiner horizontalmente */
    width: 600px; /* Define a largura do contêiner */
    margin-top: 200px; /* Define a margem superior do contêiner */
    background: #fff; /* Define a cor de fundo do contêiner */
    padding-bottom: 30px; /* Define o preenchimento inferior do contêiner */
    border-radius: 5px; /* Adiciona bordas arredondadas ao contêiner */
}

/* Estilo do cabeçalho */
.header {
    display: flex;
    flex-direction: column; /* Alinha os itens verticalmente */
    align-items: center; /* Centraliza os itens horizontalmente */
    gap: 9px; /* Espaço entre os itens */
    width: 100%; /* Define a largura do cabeçalho */
    margin-top: 30px; /* Define a margem superior do cabeçalho */
}

/* Estilo do texto do cabeçalho */
.text {
    color: #3c009d; /* Define a cor do texto */
    font-size: 48px; /* Define o tamanho da fonte */
    font-weight: 700; /* Define o peso da fonte */
}

/* Estilo da linha embaixo do texto */
.underline {
    width: 61px; /* Define a largura da linha */
    height: 6px; /* Define a altura da linha */
    background: #3c009d; /* Define a cor de fundo da linha */
    border-radius: 9px; /* Adiciona bordas arredondadas à linha */
}

/* Estilo dos campos de entrada */
.inputs {
    margin-top: 55px; /* Define a margem superior dos campos de entrada */
    display: flex;
    flex-direction: column; /* Alinha os itens verticalmente */
    gap: 25px; /* Espaço entre os campos */
}

/* Estilo individual de cada campo de entrada */
.input {
    display: flex;
    align-items: center; /* Alinha os itens verticalmente no centro */
    margin: auto; /* Centraliza o campo horizontalmente */
    width: 480px; /* Define a largura do campo */
    height: 80px; /* Define a altura do campo */
    background: #eaeaea; /* Define a cor de fundo do campo */
    border-radius: 6px; /* Adiciona bordas arredondadas ao campo */
}

/* Estilo das imagens dentro dos campos de entrada */
.input img {
    margin: 0px 30px; /* Define a margem ao redor da imagem */
}

/* Estilo dos inputs dentro dos campos de entrada */
.input input {
    height: 50px; /* Define a altura do input */
    width: 400px; /* Define a largura do input */
    background: transparent; /* Define o fundo transparente do input */
    border: none; /* Remove a borda do input */
    outline: none; /* Remove o contorno do input */
    color: #797979; /* Define a cor do texto do input */
    font-size: 19px; /* Define o tamanho da fonte do input */
}

/* Estilo da mensagem de "Esqueceu a senha?" */
.forgot-password {
    padding-left: 62px; /* Define o preenchimento à esquerda da mensagem */
    margin-top: 27px; /* Define a margem superior da mensagem */
    color: #797979; /* Define a cor do texto da mensagem */
    font-size: 18px; /* Define o tamanho da fonte da mensagem */
}

/* Estilo do texto clicável dentro da mensagem de "Esqueceu a senha?" */
.forgot-password span {
    color: #4c00b4; /* Define a cor do texto clicável */
    cursor: pointer; /* Define o cursor como uma mão para indicar um link */
}

/* Estilo do contêiner dos botões de ação */
.submit-container {
    display: flex;
    gap: 30px; /* Espaço entre os botões */
    margin: 60px auto; /* Define a margem superior e centraliza o contêiner horizontalmente */
}

/* Estilo dos botões de ação */
.submit {
    display: flex;
    justify-content: center; /* Alinha o texto horizontalmente no centro */
    align-items: center; /* Alinha o texto verticalmente no centro */
    width: 220px; /* Define a largura do botão */
    height: 59px; /* Define a altura do botão */
    color: #fff; /* Define a cor do texto do botão */
    background: #4c00b4; /* Define a cor de fundo do botão */
    border-radius: 50px; /* Adiciona bordas arredondadas ao botão */
    font-size: 19px; /* Define o tamanho da fonte do botão */
    font-weight: 700; /* Define o peso da fonte do botão */
    cursor: pointer; /* Define o cursor como uma mão para indicar que o botão é clicável */
}

/* Estilo para o botão inativo */
.gray {
    background: #EAEAEA; /* Define a cor de fundo para o botão inativo */
    color: #676767; /* Define a cor do texto para o botão inativo */
}
```

# Projeto 2 - Home page com vídeo e carrossel de fotos

### 1. Estrutura Geral

**App Component (`App.js`):**
1. **Importações**: Importa os componentes `Background`, `Navbar` e `Hero`, e usa os hooks `useEffect` e `useState` do React.
2. **Dados do Hero**: Define um array `heroData` com três conjuntos de dados de texto.
3. **Estados**: Usa `useState` para gerenciar o índice do `heroData` (`heroCount`) e o status de reprodução do vídeo (`playStatus`).
4. **Efeito Colateral**: Usa `useEffect` para atualizar `heroCount` a cada 3 segundos.
5. **Renderização**: Renderiza os componentes `Background`, `Navbar`, e `Hero`, passando os estados e dados necessários como props.

**Código (`App.js`):**
```jsx
import React, { useEffect, useState } from 'react';
import Background from './Components/Background/Background';
import Navbar from './Components/Navbar/Navbar';
import Hero from './Components/Hero/Hero';

const App = () => {
  let heroData = [
    {text1:"Dive into", text2:"what you love"},
    {text1:"Indulge", text2:"your passions"},
    {text1:"Give in to", text2:"your passions"},
  ];

  const [heroCount, setHeroCount] = useState(2);
  const [playStatus, setPlayStatus] = useState(false);

  useEffect(() => {
    const interval = setInterval(() => {
      setHeroCount((count) => (count === 2 ? 0 : count + 1));
    }, 3000);

    return () => clearInterval(interval);
  }, []);

  return (
    <div>
      <Background playStatus={playStatus} heroCount={heroCount} />
      <Navbar />
      <Hero 
        setPlayStatus={setPlayStatus}
        heroData={heroData[heroCount]}
        heroCount={heroCount}
        setHeroCount={setHeroCount}
        playStatus={playStatus}
      />
    </div>
  );
}

export default App;
```

## 2. Estilo Global

### CSS Global (`index.css`)

O arquivo `index.css` é utilizado para definir o estilo global da aplicação. Ele realiza ajustes fundamentais na aparência e no comportamento dos elementos em toda a aplicação.

**Reseta Margens e Preenchimentos:** 
Remove margens e preenchimentos padrões para garantir que o layout seja consistente e não seja influenciado por estilos predefinidos do navegador.

**Fonte e Overflow:** 
Define a fonte padrão utilizada na aplicação e evita a rolagem vertical da página.

```css
* {
  margin: 0;
  padding: 0;
  font-family: 'Poppins';
  overflow-y: hidden;
}

## 3. Componente Background

### Código (`Background.js`)

O componente `Background` é responsável por renderizar um vídeo ou uma imagem de fundo, dependendo do estado `playStatus` e do índice `heroCount`. 

**Importações:**
- Importa o arquivo CSS para estilos.
- Importa recursos de mídia, incluindo um vídeo e três imagens para o fundo.

**Componente:**
Renderiza um vídeo se `playStatus` for `true`. Caso contrário, renderiza uma imagem com base no valor de `heroCount`.

```jsx
import "./Background.css";
import video1 from "../../assets/video1.mp4";
import image1 from "../../assets/image1.png";
import image2 from "../../assets/image2.png";
import image3 from "../../assets/image3.png";

const Background = ({ playStatus, heroCount }) => {
    if (playStatus) {
        return (
            <video className="background fade-in" autoPlay loop muted>
                <source src={video1} type="video/mp4" />
            </video>
        );
    } else if (heroCount === 0) {
        return <img src={image1} className="background fade-in" alt="Background Image 1" />;
    } else if (heroCount === 1) {
        return <img src={image2} className="background fade-in" alt="Background Image 2" />;
    } else if (heroCount === 2) {
        return <img src={image3} className="background fade-in" alt="Background Image 3" />;
    }
}

export default Background;
```

### CSS (`Background.css`)

O arquivo `Background.css` define os estilos para o componente de fundo, incluindo a posição, ajuste e animação para uma transição suave entre imagens e vídeos.

#### Estilo do Background:
Define a posição do background para cobrir toda a tela e garante que o elemento de fundo fique atrás de outros conteúdos.

#### Animação de Fade-In:
Adiciona uma animação para uma transição suave de opacidade.

```css
.background {
    height: 100%;
    width: 100%;
    float: left;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    padding: none;
    position: fixed;
    object-fit: cover;
    z-index: -1;
}

@keyframes fadeIn {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

.fade-in {
    animation: fadeIn 500ms ease-in-out;
}
```

- background: Define a altura e largura do elemento de fundo para cobrir toda a tela, fixando-o atrás do conteúdo com z-index: -1.
- @keyframes fadeIn: Define a animação de transição de opacidade, que faz com que o elemento apareça suavemente.
- .fade-in: Aplica a animação de fade-in para um efeito de transição suave de opacidade.

### 5. Componente Navbar

#### Código (`Navbar.js`):

O componente `Navbar` renderiza o logo e o menu de navegação, proporcionando uma interface de navegação no topo da página.

```jsx
import "./Navbar.css";

const Navbar = () => {
  return (
    <div className="nav">
        <div className="nav-logo">EV-olution</div>
        <ul className="nav-menu">
            <li>Home</li>
            <li>Explore</li>
            <li>About</li>
            <li className="nav-content">Content</li>
        </ul>
    </div>
  );
}

export default Navbar;
```

### 5. Componente Navbar

#### Código (`Navbar.js`):

O componente `Navbar` renderiza o logo e o menu de navegação, proporcionando uma interface de navegação no topo da página.

```jsx
import "./Navbar.css";

const Navbar = () => {
  return (
    <div className="nav">
        <div className="nav-logo">EV-olution</div>
        <ul className="nav-menu">
            <li>Home</li>
            <li>Explore</li>
            <li>About</li>
            <li className="nav-content">Content</li>
        </ul>
    </div>
  );
}

export default Navbar;
```

### CSS (`Navbar.css`)

O arquivo `Navbar.css` define o estilo para o componente de navegação, incluindo o layout do logo e do menu.

```css
.nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 40px 120px;
    color: white;
}

.nav-logo {
    font-family: 'Outfit';
    font-size: 42px;
    font-weight: 400;
}

.nav-menu {
    display: flex;
    align-items: center;
    list-style: none;
    font-size: 18px;
    gap: 90px;
}

.nav-content {
    border-radius: 50px;
    padding: 10px 30px;
    background-color: #fff;
    color: black;
}
```

- .nav: Configura o layout do componente de navegação, alinhando o conteúdo no topo da página e distribuindo espaço entre o logo e o menu de navegação.
- .nav-logo: Define o estilo do logo, incluindo a fonte, tamanho e peso.
- .nav-menu: Estiliza a lista do menu de navegação, alinhando os itens e removendo os marcadores da lista.
- .nav-content: Aplica estilos adicionais ao item de menu "Content", incluindo bordas arredondadas e um fundo branco.
