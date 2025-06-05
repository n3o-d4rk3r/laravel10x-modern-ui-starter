
# Laravel 10.x + Vite + SCSS + Tailwind (Optional) Setup Guide

## Prerequisites

- PHP 8.1+
- Composer
- Node.js + npm
- Git

## 1. Create New Laravel Project

```powershell
composer create-project laravel/laravel myproject
cd myproject
```

## 2. Initialize Git (optional)

```powershell
git init
```

## 3. Install Dependencies

```powershell
npm install
```

## 4. Compile Assets with Vite

Run once to build assets:

```powershell
npm run build
```

Or for development with live reload:

```powershell
npm run dev
```

## 5. Use SCSS (SASS)

### Step 1: Rename `resources/css/app.css` to `app.scss`

```powershell
Rename-Item .\resources\css\app.css app.scss
```

### Step 2: Update `vite.config.js`

```js
// vite.config.js
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';

export default defineConfig({
    plugins: [
        laravel([
            'resources/js/app.js',
            'resources/css/app.scss',
        ]),
    ],
});
```

### Step 3: Update `app.js` to import SCSS

```js
// resources/js/app.js
import '../css/app.scss';
```

## 6. Optional: Install Tailwind CSS

```powershell
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### Configure `tailwind.config.js`

```js
// tailwind.config.js
module.exports = {
    content: [
        './resources/**/*.blade.php',
        './resources/**/*.js',
        './resources/**/*.vue',
    ],
    theme: {
        extend: {},
    },
    plugins: [],
}
```

### Update `resources/css/app.scss`

```scss
@tailwind base;
@tailwind components;
@tailwind utilities;

/* Your SCSS goes below */
```

## 7. Run Laravel Server

```powershell
php artisan serve
```

## 8. Run Frontend (Vite)

In another terminal:

```powershell
npm run dev
```

---

## Troubleshooting

### If you encounter `npx` or permission issues:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

---

## License

MIT
