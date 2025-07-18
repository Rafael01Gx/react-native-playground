<div align="center">
  <br />
    <img src="/assets/images/cover.png" alt="Banner do Projeto" width="700">
  </a>
  <br />

  <div>
    <img src="https://img.shields.io/badge/-React_Native-black?style=for-the-badge&logoColor=white&logo=react&color=61DAFB" alt="React Native" />
    <img src="https://img.shields.io/badge/-Expo-black?style=for-the-badge&logoColor=white&logo=expo&color=000020" alt="Expo" />
    <img src="https://img.shields.io/badge/-TypeScript-black?style=for-the-badge&logoColor=white&logo=typescript&color=3178C6" alt="TypeScript" />
    <img src="https://img.shields.io/badge/-Tailwind_CSS-black?style=for-the-badge&logoColor=white&logo=tailwindcss&color=06B6D4" alt="Tailwind CSS" />
    <img src="https://img.shields.io/badge/-Appwrite-black?style=for-the-badge&logoColor=white&logo=appwrite&color=F02E65" alt="Appwrite" />
  </div>

<h3 align="center">Aplicativo para Descoberta de Filmes com Busca Avançada</h3>

  <div align="center">
    Construa este projeto passo a passo com o tutorial completo no canal <a href="https://www.youtube.com/@javascriptmastery/videos" target="_blank"><b>JavaScript Mastery</b></a>. Junte-se à comunidade JSM!
  </div>
</div>

## 📋 <a name="table">Índice</a>

1. 🤖 [Introdução](#introducao)
2. ⚙️ [Tecnologias Utilizadas](#tech-stack)
3. 🔋 [Funcionalidades](#features)
4. 🤸 [Início Rápido](#quick-start)
5. 🕸️ [Trechos de Código](#snippets)
6. 🔗 [Recursos](#links)
7. 🚀 [Mais Informações](#more)


## <a name="introducao">🤖 Introdução</a>

Construído com Expo, TypeScript e Tailwind CSS, este app consome dados da API de filmes e implementa um algoritmo de popularidade usando Appwrite. Ele proporciona aos usuários uma navegação fluida, classificando os filmes com base em diferentes métricas de engajamento. A interface é moderna, responsiva e escalável para uso real.

## <a name="tech-stack">⚙️ Tecnologias Utilizadas</a>

- Expo
- React Native
- Appwrite
- TypeScript
- Tailwind CSS

## <a name="features">🔋 Funcionalidades</a>

### Principais recursos do aplicativo:

👉 **Dados em tempo real**: consumo e exibição de filmes atualizados  
👉 **Tela inicial**: filmes em destaque e recomendações  
👉 **Busca**: encontre filmes pelo nome  
👉 **Algoritmo de popularidade**: classifica filmes com base nas pesquisas dos usuários

...e muito mais, incluindo arquitetura de código reutilizável.

## <a name="quick-start">🤸 Início Rápido</a>

Siga os passos abaixo para rodar o projeto localmente:

### Pré-requisitos

Certifique-se de ter instalado:

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/en)
- [npm](https://www.npmjs.com/)

### Clonando o Repositório

```bash
git clone https://github.com/Rafael01Gx/react-native-playground.git
cd react-native-playground

**Instalação**

Instale as dependências do projeto usando npm:

```bash

npm install

```

**Configuração das Variáveis de Ambiente**

Crie um novo arquivo com nome `.env` na raiz do projeto e adicione:

```env

EXPO_PUBLIC_MOVIE_API_KEY=

EXPO_PUBLIC_APPWRITE_PROJECT_ID=

EXPO_PUBLIC_APPWRITE_DATABASE_ID=

EXPO_PUBLIC_APPWRITE_COLLECTION_ID=



```

Substitua os valores do espaço reservado pela sua chave de API do TMDB, ID do projeto Appwrite, ID do banco de dados e ID da coleção. Você pode obter essas credenciais cadastrando-se no [Appwrite](https://cloud.appwrite.io/console/login), [TMDB](https://www.themoviedb.org/login).

**Executando o Projeto**

```bash

npx expo start

```


Abra o aplicativo ExpoGO no seu telefone e escaneie o código QR para visualizar o projeto.

## <a name="snippets">🕸️ Trechos de Código</a>

<details>

<summary><code>tailwind.config.js</code></summary>

```typescript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./app/**/*.{js,jsx,ts,tsx}", "./components/**/*.{js,jsx,ts,tsx}"],
  presets: [require("nativewind/preset")],
  theme: {
    extend: {
      colors: {
        primary: "#030014",
        secondary: "#151312",
        ratingBox: "#221F3D",
        searchBar: "#0F0D23",
        text: "#9CA4AB",
        darkAccent: "#AB8BFF",
        accentText: "#A8B5DB",
        secondaryText: "#D6C7FF",
      },
    },
  },
  plugins: [],
};
```

</details>

<details>

<summary><code>app/globals.css</code></summary>

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

</details>

<details>

<summary><code>interfaces/interfaces.d.ts</code></summary>

```typescript
interface Movie {
  id: number;
  title: string;
  adult: boolean;
  backdrop_path: string;
  genre_ids: number[];
  original_language: string;
  original_title: string;
  overview: string;
  popularity: number;
  poster_path: string;
  release_date: string;
  video: boolean;
  vote_average: number;
  vote_count: number;
}

interface TrendingMovie {
  searchTerm: string;
  movie_id: number;
  title: string;
  count: number;
  poster_url: string;
}

interface MovieDetails {
  adult: boolean;
  backdrop_path: string | null;
  belongs_to_collection: {
    id: number;
    name: string;
    poster_path: string;
    backdrop_path: string;
  } | null;
  budget: number;
  genres: {
    id: number;
    name: string;
  }[];
  homepage: string | null;
  id: number;
  imdb_id: string | null;
  original_language: string;
  original_title: string;
  overview: string | null;
  popularity: number;
  poster_path: string | null;
  production_companies: {
    id: number;
    logo_path: string | null;
    name: string;
    origin_country: string;
  }[];
  production_countries: {
    iso_3166_1: string;
    name: string;
  }[];
  release_date: string;
  revenue: number;
  runtime: number | null;
  spoken_languages: {
    english_name: string;
    iso_639_1: string;
    name: string;
  }[];
  status: string;
  tagline: string | null;
  title: string;
  video: boolean;
  vote_average: number;
  vote_count: number;
}

interface TrendingCardProps {
  movie: TrendingMovie;
  index: number;
}
```

</details>

## <a name="links">🔗 Assets</a>

- Os arquivos utilizados neste projeto estão localizados na pasta [`assets/`](./assets/) do repositório.

## <a name="more">🙏 Créditos</a>

Este projeto foi inspirado e baseado no conteúdo criado por [JavaScript Mastery](https://www.youtube.com/@javascriptmastery).  
Agradecimentos especiais à equipe do canal pelo incrível trabalho educativo e pelos tutoriais de alta qualidade que tornam o aprendizado acessível, moderno e prático para a comunidade de desenvolvedores.

> Siga o canal e acompanhe os tutoriais: [JavaScript Mastery no YouTube](https://www.youtube.com/@javascriptmastery)
