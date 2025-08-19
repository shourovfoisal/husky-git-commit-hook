## Source
https://vjnvisakh.medium.com/setting-up-pre-commit-hooks-using-husky-a84888a2667a

<br>

This is a **Vite Project** created with:  

```bash
npm create vite@latest
```

Steps:

1. Initiate git
```bash
git init
```

2. Install and Initiate Husky
```bash
npm install --save-dev husky
npx husky init
```

3. Add the following command to the 'scripts' field of the package.json file
```bash
"lint": "eslint \"{src,apps,libs,test}/**/*.ts\" --fix"
```

4. Inside the generated husky folder in the root directory, open the file pre-commit in a text editor, and paste the command text `npm run lint`