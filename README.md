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
import React, { useEffect, useState } from 'react'; // Importa React e hooks necessários
import Background from './Components/Background/Background'; // Importa o componente Background
import Navbar from './Components/Navbar/Navbar'; // Importa o componente Navbar
import Hero from './Components/Hero/Hero'; // Importa o componente Hero

const App = () => {
  // Define os dados para o componente Hero
  let heroData = [
    { text1: "Dive into", text2: "what you love" },
    { text1: "Indulge", text2: "your passions" },
    { text1: "Give in to", text2: "your passions" },
  ];

  // Cria um estado para controlar o índice da imagem ou vídeo de fundo
  const [heroCount, setHeroCount] = useState(2);

  // Cria um estado para controlar o status de reprodução do vídeo
  const [playStatus, setPlayStatus] = useState(false);

  useEffect(() => {
    // Define um intervalo que muda o índice do herói a cada 3 segundos
    const interval = setInterval(() => {
      setHeroCount((count) => (count === 2 ? 0 : count + 1));
    }, 3000);

    // Limpa o intervalo quando o componente é desmontado
    return () => clearInterval(interval);
  }, []);

  return (
    <div>
      {/* Renderiza o componente Background, passando os estados playStatus e heroCount */}
      <Background playStatus={playStatus} heroCount={heroCount} />
      
      {/* Renderiza o componente Navbar */}
      <Navbar />
      
      {/* Renderiza o componente Hero, passando os dados e estados necessários */}
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
```

## 3. Componente Background

### Código (`Background.js`)

O componente `Background` é responsável por renderizar um vídeo ou uma imagem de fundo, dependendo do estado `playStatus` e do índice `heroCount`. 

**Importações:**
- Importa o arquivo CSS para estilos.
- Importa recursos de mídia, incluindo um vídeo e três imagens para o fundo.

**Componente:**
Renderiza um vídeo se `playStatus` for `true`. Caso contrário, renderiza uma imagem com base no valor de `heroCount`.

```jsx
import "./Background.css"; // Importa o arquivo de estilos CSS para o componente
import video1 from "../../assets/video1.mp4"; // Importa o arquivo de vídeo para o fundo
import image1 from "../../assets/image1.png"; // Importa a primeira imagem de fundo
import image2 from "../../assets/image2.png"; // Importa a segunda imagem de fundo
import image3 from "../../assets/image3.png"; // Importa a terceira imagem de fundo

const Background = ({ playStatus, heroCount }) => {
    // Verifica se o playStatus está ativado
    if (playStatus) {
        // Se playStatus for verdadeiro, renderiza o vídeo como fundo
        return (
            <video className="background fade-in" autoPlay loop muted>
                <source src={video1} type="video/mp4" /> {/* Define o vídeo a ser reproduzido */}
            </video>
        );
    } 
    // Se playStatus não estiver ativado, verifica o valor de heroCount
    else if (heroCount === 0) {
        // Se heroCount for 0, renderiza a primeira imagem como fundo
        return <img src={image1} className="background fade-in" alt="Background Image 1" />;
    } 
    else if (heroCount === 1) {
        // Se heroCount for 1, renderiza a segunda imagem como fundo
        return <img src={image2} className="background fade-in" alt="Background Image 2" />;
    } 
    else if (heroCount === 2) {
        // Se heroCount for 2, renderiza a terceira imagem como fundo
        return <img src={image3} className="background fade-in" alt="Background Image 3" />;
    }
}

export default Background; // Exporta o componente para ser utilizado em outras partes da aplicação
```

### CSS (`Background.css`)

O arquivo `Background.css` define os estilos para o componente de fundo, incluindo a posição, ajuste e animação para uma transição suave entre imagens e vídeos.

#### Estilo do Background:
Define a posição do background para cobrir toda a tela e garante que o elemento de fundo fique atrás de outros conteúdos.

#### Animação de Fade-In:
Adiciona uma animação para uma transição suave de opacidade.

```css
/* Estiliza o fundo para ocupar toda a tela */
.background {
    height: 100%; /* Define a altura do fundo para 100% da altura da tela */
    width: 100%; /* Define a largura do fundo para 100% da largura da tela */
    float: left; /* Flutua o elemento para a esquerda */
    top: 0; /* Define a posição superior do fundo para 0 */
    left: 0; /* Define a posição esquerda do fundo para 0 */
    right: 0; /* Define a posição direita do fundo para 0 */
    bottom: 0; /* Define a posição inferior do fundo para 0 */
    padding: none; /* Remove qualquer preenchimento */
    position: fixed; /* Fixar o fundo para que ele não se mova ao rolar a página */
    object-fit: cover; /* Faz com que o conteúdo do fundo cubra completamente o elemento, mantendo a proporção */
    z-index: -1; /* Define o índice z para que o fundo fique atrás dos outros conteúdos */
}

/* Define a animação de fade-in */
@keyframes fadeIn {
    from {
        opacity: 0; /* Começa com opacidade 0 (invisível) */
    }
    to {
        opacity: 1; /* Termina com opacidade 1 (visível) */
    }
}

/* Aplica a animação de fade-in ao elemento */
.fade-in {
    animation: fadeIn 500ms ease-in-out; /* Define a duração da animação para 500ms e a curva de velocidade como ease-in-out */
}
```

- background: Define a altura e largura do elemento de fundo para cobrir toda a tela, fixando-o atrás do conteúdo com z-index: -1.
- @keyframes fadeIn: Define a animação de transição de opacidade, que faz com que o elemento apareça suavemente.
- .fade-in: Aplica a animação de fade-in para um efeito de transição suave de opacidade.

### 4. Componente Hero

#### Código (`Hero.jsx`):

O componente `Navbar` renderiza o logo e o menu de navegação, proporcionando uma interface de navegação no topo da página.

```jsx
// Importa o arquivo de estilo CSS para o componente Hero
import "./Hero.css";

// Importa as imagens dos ícones e botões
import arrow_btn from '../../assets/arrow_btn.png';
import play_icon from '../../assets/play_icon.png';
import pause_icon from '../../assets/pause_icon.png';

// Define o componente Hero que recebe várias propriedades
const Hero = ({ heroData, setHeroCount, heroCount, setPlayStatus, playStatus }) => {
  return (
    <div className="hero">
        {/* Renderiza o texto do hero */}
        <div className="hero-text">
             <p>{heroData.text1}</p>
             <p>{heroData.text2}</p>
        </div>
        {/* Renderiza a seção de exploração */}
        <div className="hero-explore">
            <p>Explore the features</p>
            <img src={arrow_btn} alt="Explore Button"/>
        </div>
        {/* Renderiza os pontos de navegação e o controle de vídeo */}
        <div className="hero-dot-play">
            <ul className="hero-dots">
                {/* Pontos de navegação para alternar entre os heróis */}
                <li onClick={() => setHeroCount(0)} className={heroCount === 0 ? "hero-dot orange" : "hero-dot"}></li>
                <li onClick={() => setHeroCount(1)} className={heroCount === 1 ? "hero-dot orange" : "hero-dot"}></li>
                <li onClick={() => setHeroCount(2)} className={heroCount === 2 ? "hero-dot orange" : "hero-dot"}></li>
            </ul>
            <div className="hero-play">
                {/* Botão de Play/Pause para o vídeo */}
                <img onClick={() => setPlayStatus(!playStatus)} src={playStatus ? pause_icon : play_icon} alt="Play/Pause Button"/>
                <p>See the video</p>
            </div>
        </div>
    </div>
  );
}

// Exporta o componente Hero como padrão
export default Hero;
```

### CSS (`Hero.css`)

O arquivo `Navbar.css` define o estilo para o componente de navegação, incluindo o layout do logo e do menu.
```
/* Define margens para o container principal do componente hero */
.hero {
    margin: 0px 120px;      /* Margem horizontal de 120px */
    margin-top: 270px;      /* Margem superior de 270px */
}

/* Estiliza o texto dentro do componente hero */
.hero-text {
    color: #FFF;            /* Cor do texto branco */
    font-size: 110px;       /* Tamanho da fonte grande (110px) */
    font-weight: 500;       /* Peso da fonte médio */
    line-height: 130px;     /* Altura da linha para espaçamento */
}

/* Estiliza a seção "explore" do componente hero */
.hero-explore {
    display: flex;          /* Usa flexbox para o layout */
    align-items: center;    /* Alinha os itens ao centro verticalmente */
    gap: 50px;              /* Espaço entre os itens de 50px */
    width: fit-content;     /* Largura ajustada ao conteúdo */
    margin-top: 70px;       /* Margem superior de 70px */
    padding: 5px 8px;       /* Padding interno */
    padding-left: 30px;     /* Padding adicional à esquerda */
    border-radius: 60px;    /* Bordas arredondadas */
    background-color: white; /* Fundo branco */
    cursor: pointer;        /* Aponta o cursor para indicar que é clicável */
}

/* Estiliza o parágrafo dentro da seção "explore" */
.hero-explore p {
    color: #292929;         /* Cor do texto */
    font-size: 20px;        /* Tamanho da fonte */
    font-weight: 500;       /* Peso da fonte */
}

/* Define o layout para a seção de pontos e botão de reprodução */
.hero-dot-play {
    margin: 120px;          /* Margem de 120px em todas as direções */
    display: flex;          /* Usa flexbox para o layout */
    justify-content: space-between; /* Espaça os itens igualmente */
}

/* Estiliza a lista de pontos de navegação */
.hero-dots {
    display: flex;          /* Usa flexbox para o layout */
    align-items: center;    /* Alinha os itens ao centro verticalmente */
    gap: 23px;              /* Espaço entre os pontos */
    list-style: none;       /* Remove os marcadores de lista */
}

/* Estiliza cada ponto individualmente */
.hero-dot {
    width: 15px;            /* Largura do ponto */
    height: 15px;           /* Altura do ponto */
    background-color: #fff; /* Cor de fundo branca */
    border-radius: 7.5px;   /* Bordas arredondadas */
    cursor: pointer;        /* Aponta o cursor para indicar que é clicável */
}

/* Estiliza os pontos ativos com cor laranja */
.hero-dot.orange {
    background: orangered;  /* Cor de fundo laranja */
}

/* Estiliza a seção de controle de reprodução */
.hero-play {
    display: flex;          /* Usa flexbox para o layout */
    align-items: center;    /* Alinha os itens ao centro verticalmente */
    gap: 30px;              /* Espaço entre os itens */
}

/* Estiliza o parágrafo dentro da seção de reprodução */
.hero-play p {
    color: white;           /* Cor do texto branca */
    font-size: 19px;        /* Tamanho da fonte */
}

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
/* Estiliza o container de navegação */
.nav {
    display: flex; /* Usa Flexbox para layout flexível */
    justify-content: space-between; /* Distribui espaço igualmente entre os itens, alinhando-os nas extremidades */
    align-items: center; /* Alinha os itens verticalmente no centro */
    margin: 40px 120px; /* Define margens superior e inferior de 40px e margens esquerda e direita de 120px */
    color: white; /* Define a cor do texto para branco */
}

/* Estiliza o logo de navegação */
.nav-logo {
    font-family: 'Outfit'; /* Define a fonte do logo */
    font-size: 42px; /* Define o tamanho da fonte para 42px */
    font-weight: 400; /* Define o peso da fonte para 400 (normal) */
}

/* Estiliza o menu de navegação */
.nav-menu {
    display: flex; /* Usa Flexbox para layout flexível */
    align-items: center; /* Alinha os itens verticalmente no centro */
    list-style: none; /* Remove os marcadores da lista */
    font-size: 18px; /* Define o tamanho da fonte para 18px */
    gap: 90px; /* Define um espaçamento de 90px entre os itens do menu */
}

/* Estiliza o item de menu "Content" */
.nav-content {
    border-radius: 50px; /* Adiciona bordas arredondadas com raio de 50px */
    padding: 10px 30px; /* Adiciona preenchimento interno de 10px no topo e embaixo e 30px nas laterais */
    background-color: #fff; /* Define a cor de fundo para branco */
    color: black; /* Define a cor do texto para preto */
}
```

- .nav: Configura o layout do componente de navegação, alinhando o conteúdo no topo da página e distribuindo espaço entre o logo e o menu de navegação.
- .nav-logo: Define o estilo do logo, incluindo a fonte, tamanho e peso.
- .nav-menu: Estiliza a lista do menu de navegação, alinhando os itens e removendo os marcadores da lista.
- .nav-content: Aplica estilos adicionais ao item de menu "Content", incluindo bordas arredondadas e um fundo branco.
