## Source

https://vjnvisakh.medium.com/setting-up-pre-commit-hooks-using-husky-a84888a2667a

<br>

This is a **Vite Project** created with:

```bash
npm create vite@latest
```

Steps:

1. **Initiate git**

```bash
git init
```

2. **Install and Initiate Husky**

```bash
npm install --save-dev husky
npx husky init
```

3. **Install and Init eslint**

```bash
npm install --save-dev eslint
npm init @eslint/config@latest
```

4. **Install and configure prettier**

```bash
npm install --save-dev prettier
```

Add the `.prettierrc` file, and use the sample config

```json
{
  "semi": true,
  "singleQuote": true,
  "trailingComma": "es5",
  "printWidth": 100
}
```

Add the `.prettierignore` file, and ignore directories like dependencies and builds etc.

```
node_modules
.next
dist
build
```

5. **Add the following eslint command scripts to the 'scripts' field of the package.json file**

```json
"lint": "eslint \"{src,apps,libs,test}/**/*.{js,jsx,ts,tsx,json}\" --fix"
```

or

```json
"lint": "eslint . --ext .js,.jsx,.ts,.tsx --fix"
```

6. **Add the following prettier command scripts to the same file**

```json
"format": "prettier --write .",
"format:check": "prettier --check ."
```

7. **Inside the generated `.husky` folder in the root directory, open the file `pre-commit` in a text editor, and paste the commands**

```bash
npm run lint
npm run format:check
```

<br>
<hr>
<br>

> Now upon git commit, eslint will possibly fix erroneous code where possible, and block the commit for those it can't.

> After the linting check, prettier formatting-check will run. If the formatting requirement passes, the commit is done. Else the commit fails. If it fails, `npm run format` will make prettier fix all formatting issues.
