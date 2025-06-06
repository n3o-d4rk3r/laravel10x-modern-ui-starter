

# Laravel 10.x + Vite + SCSS + Tailwind (Optional) Setup Guide

## Prerequisites

- PHP 8.1+
- Composer
- Node.js + npm
- Git

## 1. Create New Laravel Project

```Visual Studio Cmnd, Git Bash and etc
composer create-project laravel/laravel your-project-name "10.*"
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

### Unable to Run npx tailwindcss init -p - "Could Not Determine Executable to Run"

<blockquote>
<p dir="auto">The <code class="notranslate">init</code> command no longer exists in v4. Consider checking <a href="https://tailwindcss.com/docs/installation/using-vite" rel="nofollow">the installation documentation</a> that is most relevant to your project to integrate Tailwind v4.</p>
<p dir="auto">If you are trying to use v3, ensure the version qualifier is used:</p>
<div class="highlight highlight-source-shell notranslate position-relative overflow-auto" dir="auto"><pre class="notranslate">$ npm install -D tailwindcss@3 postcss autoprefixer
$ npx tailwindcss init -p</pre><div class="zeroclipboard-container position-absolute right-0 top-0">
    <clipboard-copy aria-label="Copy" class="ClipboardButton btn js-clipboard-copy m-2 p-0" data-copy-feedback="Copied!" data-tooltip-direction="w" value="$ npm install -D tailwindcss@3 postcss autoprefixer
$ npx tailwindcss init -p" tabindex="0" role="button" style="display: inherit;">
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-copy js-clipboard-copy-icon m-2">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
</svg>
      <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-check js-clipboard-check-icon color-fg-success d-none m-2">
    <path d="M13.78 4.22a.75.75 0 0 1 0 1.06l-7.25 7.25a.75.75 0 0 1-1.06 0L2.22 9.28a.751.751 0 0 1 .018-1.042.751.751 0 0 1 1.042-.018L6 10.94l6.72-6.72a.75.75 0 0 1 1.06 0Z"></path>
</svg>
    </clipboard-copy>
  </div></div>
</blockquote>

### If you encounter `npx` or permission issues:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```


---

## License

MIT
