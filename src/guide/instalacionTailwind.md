# Instalar y configurar Tailwind CSS en un proyecto en Next.js

## Instalación

En la terminal escribimos lo siguiente: 

```bash
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
```

## Creación de los archivos de configuración

Esto generará los archivos `tailwind.config.js` y `postcss.config.js`

```bash
npx tailwindcss init -p
```

## Configurando los archivos

Abrimos el archivo `taiwind.config.js` y editamos lo siguiente:
```js
module.exports = {
-   purge: [],
+   purge: ['./page/**/*.{js, ts, jsx, tsx}', './components/**/*.{js,ts,jsx,tsx}'],
    darkMode: false, //or 'media' or 'class'
    theme: {
        extend: {},
    },
    variants: {
        extend: {},
    },
    plugins: []
}
```

Luego en el archivo `globals.css` ubicado en la carpeta styles eliminar todo y agregar:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Además eliminar el archivo `Home.modules.css`, ya no nos servirá en el proyecto.

Luego ir al archivo `index.js` ubicado en la carpeta `pages` y eliminar la instancia de los estilos que acabamos de elimiar y todas sus herencias, es decir, pasar de esto:

```js
import Head from 'next/head'
import styles from '../styles/Home.module.css'

export default function Home() {
  return (
    <div className={styles.container}>
      <Head>
        <title>Create Next App</title>
        <link rel="icon" href="/favicon.ico" />
      </Head>

      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to <a href="https://nextjs.org">Next.js!</a>
        </h1>

        <p className={styles.description}>
          Get started by editing{' '}
          <code className={styles.code}>pages/index.js</code>
        </p>

        <div className={styles.grid}>
          <a href="https://nextjs.org/docs" className={styles.card}>
            <h3>Documentation &rarr;</h3>
            <p>Find in-depth information about Next.js features and API.</p>
          </a>

          <a href="https://nextjs.org/learn" className={styles.card}>
            <h3>Learn &rarr;</h3>
            <p>Learn about Next.js in an interactive course with quizzes!</p>
          </a>

          <a
            href="https://github.com/vercel/next.js/tree/master/examples"
            className={styles.card}
          >
            <h3>Examples &rarr;</h3>
            <p>Discover and deploy boilerplate example Next.js projects.</p>
          </a>

          <a
            href="https://vercel.com/new?utm_source=create-next-app&utm_medium=default-template&utm_campaign=create-next-app"
            className={styles.card}
          >
            <h3>Deploy &rarr;</h3>
            <p>
              Instantly deploy your Next.js site to a public URL with Vercel.
            </p>
          </a>
        </div>
      </main>

      <footer className={styles.footer}>
        <a
          href="https://vercel.com?utm_source=create-next-app&utm_medium=default-template&utm_campaign=create-next-app"
          target="_blank"
          rel="noopener noreferrer"
        >
          Powered by{' '}
          <img src="/vercel.svg" alt="Vercel Logo" className={styles.logo} />
        </a>
      </footer>
    </div>
  )
}

```

A esto:

```js
import Head from "next/head";

export default function Home() {
	return <></>;
}
```
