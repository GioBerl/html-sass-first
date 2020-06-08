tramite terminale **<u><mark>entra nella cartella di progetto</mark></u>**. una volta dentro, copia (Ctrl + C) e incolla (Ctrl + V) interamente:

## Per Windows (powershell)
```bash
npm init -y;
npm install laravel-mix --save-dev;
cp node_modules/laravel-mix/setup/webpack.mix.js ./;
touch .gitignore;
echo "node_modules/`rpackage-lock.json" >> .gitignore;
mkdir src;
cd src;
mkdir js scss;
cd js;
touch app.js;
cd ../scss;
touch app.scss;
cd ../..;
npm install cross-env --save-dev;
touch index.html
```

## Per Mac e Linux 
```bash
npm init -y;
npm install laravel-mix --save-dev;
cp node_modules/laravel-mix/setup/webpack.mix.js ./;
touch .gitignore;
echo ".DS_Store\nnode_modules/\npackage-lock.json" >> .gitignore;
mkdir src;
cd src;
touch app.js app.scss;
cd ..;
npm install cross-env --save-dev;
touch index.html
```

dentro il file *webpack.mix.js* sostituisci la riga 

```js
mix.js("src/app.js", "dist/").sass("src/app.scss", "dist/");
```

con

```js
mix.js("src/app.js", "public/").sass("src/app.scss", "public/");
```

poi nel file *package.json* al posto di

```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
 }
```

incolla

```json
"scripts": {
        "dev": "npm run development",
        "development": "cross-env NODE_ENV=development node_modules/webpack/bin/webpack.js --progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js",
        "watch": "npm run development -- --watch",
        "hot": "cross-env NODE_ENV=development node_modules/webpack-dev-server/bin/webpack-dev-server.js --inline --hot --config=node_modules/laravel-mix/setup/webpack.config.js",
        "prod": "npm run production",
        "production": "cross-env NODE_ENV=production node_modules/webpack/bin/webpack.js --no-progress --hide-modules --config=node_modules/laravel-mix/setup/webpack.config.js"
}
```

nel file *index.html* ricorda di aggiungere nell' head:

```html
<link rel="stylesheet" href="public/app.css">
```

salva e ora dovresti poter usare

```bash
npm run dev
```
