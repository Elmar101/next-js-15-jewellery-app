- ESLINT => https://eslint.org/
- ESLINT STYLE => https://eslint.style/packages/ts
- PRETTIER => https://prettier.io/
- PRE-COMMIT => https://prettier.io/docs/precommit
- LINT STAGED => https://github.com/lint-staged/lint-staged

# ESLINT + PRETTIER (https://www.youtube.com/watch?v=F0IrHtPo-Ec&list=PL1TrjkMQ8UbVjig1BXDBo1oMzMgVc5I_a)

# ESLINT configuration

1. npm install eslint --save-dev
2. npx eslint --init (some question we will answer)
3. npx eslint . (check all files we can use . instead of file name ex: npx eslint src/index.js) we dont download eslint global thats why dont run "eslint" command (eslint --init -> dont work) now we use npx eslint --init if we want to check one file we can use "npx eslint (file-name)"
4. open "package.json" and add "lint": "eslint . --ext .js, .ts, .jsx, .tsx, .json, .cjs, .vue" in "scripts" ext -> extension (fayl uzantisi) now we can use "npm run lint" -> check all files because we add "eslint ." ex: "lint": "eslint src --ext .js, .ts, .jsx, .tsx, .json, .cjs, .vue" "lint": "eslint (directory-name) --ext .js, .ts, .jsx, .tsx, .json, .cjs, .vue --fix" => "lint": "eslint . --ext .js, .ts, .jsx, .tsx, .json, .cjs, .vue"

## NEW VERSION WE DONT NEED TO ADD EXTENSIONS IN package.json SCRIPTS ("lint": "eslint ." or "lint" : "eslint src" )

5. we need display eslint errors in vscode or editor tools that why we need to install eslint plugin(Extensions) in vscode or other editor tools opening Extension and search ESLint and install -> we chhose ESLint (microsift)
6. create .eslintignore => we need to some folder dont show eslint errors in vscode or editor tools that why we need to create .eslintignore file and add folder name in .eslintignore
7. "lint:fix": "eslint . --ext .js, .ts, .jsx, .tsx, .json, .cjs, .vue --fix" (we can use "npm run lint:fix" command) fixed all eslint errors added this "lint:fix": "eslint . --ext .js, .ts --fix" script in scripts of "package.json" . - is directory name (directory name is "src", pages, components, utils, etc) --ext .js, .ts, .jsx, .tsx, .json, .cjs, .vue => we can add extension name

## NEW VERSION WE DONT NEED TO ADD EXTENSIONS IN package.json SCRIPTS ("lint:fix": "eslint . --fix" or "lint:fix" : "eslint src --fix" )

8. we open "settings.json" -> "editor.codeActionsOnSave": { "source.fixAll.eslint": true } this is for save and fix all eslint errors

# PRETTIER configuration

1. npm install --save-dev --save-exact prettier | bun add --dev --exact prettier | pnpm add --save-dev --save-exact prettier | yarn add --dev --exact prettier
2. Then, create an empty config file to let editors and other tools know you are using Prettier: epen terminal and run following script node --eval "fs.writeFileSync('.prettierrc','{}\n')"
3. Next, create a .prettierignore file to let the Prettier CLI and editors know which files to not format. Here’s an example: node --eval "fs.writeFileSync('.prettierignore','# Ignore artifacts:\nbuild\ncoverage\n')"
4. Now, format all files with Prettier: => npx prettier . --write | bun exec prettier . --write | pnpm exec prettier . --write | yarn exec prettier . --write . - is directory name (directory name is "src", pages, components, utils, etc) ex: prettier --write app/components/Button.js prettier --write . is great for formatting everything, but for a big project it might take a little while. You may run prettier --write app/ to format a certain directory, or prettier --write app/components/Button.js to format a certain file. Or use a glob like prettier --write "app/\*_/_.test.js" to format all tests in a directory (see fast-glob for supported glob syntax). If you have a CI setup, run the following as part of it to make sure that everyone runs Prettier. This avoids merge conflicts and other collaboration issues! npx prettier . --check --check is like --write, but only checks that files are already formatted, rather than overwriting them. prettier --write and prettier --check are the most common ways to run Prettier.
5. Git hooks In addition to running Prettier from the command line (prettier --write), checking formatting in CI, and running Prettier from your editor, many people like to run Prettier as a pre-commit hook as well. This makes sure all your commits are formatted, without having to wait for your CI build to finish. For example, you can do the following to have Prettier run before each commit: npm install --save-dev husky lint-staged npx husky init node --eval "fs.writeFileSync('.husky/pre-commit','npx lint-staged\n')" or bun add --dev husky lint-staged bunx husky init bun --eval "fs.writeFileSync('.husky/pre-commit','bunx lint-staged\n')"
6. Add the following to your package.json: "lint-staged": { "\*_/_": "prettier --write --ignore-unknown" } prettier --write faylları avtomatik formatlaşdırır. prettier --check isə sadəcə formatlama vəziyyətini yoxlayır və CI mühitlərində istifadə üçün idealdır.

# (https://github.com/prettier/eslint-config-prettier)

## eslint-config-prettier - is used to prevent conflicts when using ESLint and Prettier in the same project.

ESLint ilə Prettier-i eyni layihədə istifadə edərkən yaranan konfliktlərin qarşısını almaq üçün istifadə olunur.

ESLint and Prettier sometimes conflict when used together, as both try to apply stylistic rules to the code at the same time. ESLint və Prettier birlikdə istifadə edilərkən bəzən konfliktlər yaradır, çünki hər ikisi eyni vaxtda kodun formatlama (stylistic) qaydalarını tətbiq etməyə çalışır.

Since Prettier does the formatting automatically, ESLint's formatting rules are no longer needed and conflicting. Prettier avtomatik formatlama etdiyi üçün, ESLint-in formatlama qaydaları artıq lazımsız və konfliktə səbəb olur.

eslint-config-prettier prevents these conflicts and automatically disables all ESLint formatting rules. eslint-config-prettier isə bu konfliktlərin qarşısını alır və ESLint-in formatlama ilə bağlı bütün qaydalarını avtomatik söndürür.

1. npm i -D eslint-config-prettier | bun add -D eslint-config-prettier | bun add -D eslint-config-prettier | yarn add -D eslint-config-prettier

## eslint-plugin-prettier - is used to integrate Prettier into ESLint.

ESLint-in Prettier-ə inteqrasiya etmək üçün istifadə olunur.

1. npm install --save-dev eslint-plugin-prettier eslint-config-prettier -D | bun add -D eslint-plugin-prettier eslint-config-prettier | pnpm add -D eslint-plugin-prettier eslint-config-prettier | yarn add -D eslint-plugin-prettier eslint-config-prettier
2. npm install --save-dev --save-exact prettier | bun add --save-dev --save-exact prettier | pnpm add --save-dev --save-exact prettier | yarn add --save-dev --save-exact prettier

3. add "plugin:prettier/recommended" in extends from eslintConfig extends: ["next/core-web-vitals", "next/typescript", "plugin:prettier/recommended"] -> old wersion of eslintConfig new version we add -> import eslintConfigPrettier from "eslint-config-prettier/flat"; and add eslintConfigPrettier this line to extends in eslint.config.js
4. "format": "prettier src --write \"\*_/_.{ts,tsx,js,jsx,json,md,css,scss}\"", add this line to package.json of scripts or "format": "prettier . --write" dont need extension "format": "prettier . --write" . is for all files (we can write folder name like src)' now we can remove "source.fixAll.eslint": true this line in "editor.codeActionsOnSave" from settings.json
5. npm run format | bun run format | pnpm run format | yarn run format

6. we can download Prettier extension in VSCode or other tools after we add "editor.defaultFormatter": "esbenp.prettier-vscode" and "editor.formatOnSave: true in settings.json

# HUSKY (https://www.youtube.com/watch?v=Z-ZeBrZ6f5U) HUSKY+ lint-staged => (https://www.youtube.com/watch?v=bL5GaBjKAAw)

1. npm i -D husky npx husky init entered
2. .husky folder and pre-commit add this line (npm run lint | bun run lint )
3. npm install lint-staged -D AND npm install @commitlint/cli @commitlint/config-conventional --save-dev npm install -D @commitlint/config-conventional @commitlint/cli create commitlint.config.js file and add this line module.exports = { extends: ['@commitlint/config-conventional'] }
4. git commit -m"fix: foo" --no-verify -> skip husky commit

## STYLELINT -> Linting CSS (https://stylelint.io/user-guide/get-started)

1. npm init stylelint -D
2. npx stylelint "\*_/_.css"
3. add the following scripts to package.json  
   "stylelint": "stylelint src/**/\*.{css,scss}", "stylelint:fix": "stylelint src/**/\*.{css,scss} --fix"
4. we install stylelint extenssion for VSCode or other tools that we show errors and warnings in VSCode or other tools

## TYPESCRIPT ESLINT RULES => http://typescript-eslint.io/rules/no-explicit-any/

# --------------------------------------------------------------------------------------------------------------------

# Static Assets in `public`

Next.js can serve static files, like images, under a folder called public in the root directory. Files inside public can then be referenced by your code starting from the base URL (/). For example, the file public/avatars/me.png can be viewed by visiting the /avatars/me.png path. The code to display that image might look like


----------------------------------------------------------------------AZERBAYCANCA-------------------------------------------------------------------------------------------------------------
# ESLint nədir?
ESLint — JavaScript və TypeScript kodlarını yoxlayan və səhvləri göstərən bir linting (kod keyfiyyətini yoxlama) alətidir.
Kodun düzgün yazılmasını təmin edir.
Səhvləri tapır, xəbərdarlıq edir.
Kod standartlarına uyğunluğu təmin edir.

# ESLint qurulması (configuration)
npm install eslint --save-dev | bun add eslint --save-dev  | yarn add eslint --save-dev | npx add eslint --save-dev

npx ilə qlobal ESLint yükləmədən işlədilir.(ve ya diger paketler yuklemeden istifade edilir)

# İlkin qurulum üçün ESLint-ə sorğular verilir( npx eslint --init )
npx eslint --init => Bu əmri işlətdikdə sizə sorğular verilir: hansı layihə növü, hansı stil, hansı framework, hansı fayl tipinə baxmaq istədiyiniz və s.

# Kod yoxlama əmri( npx eslint . )
npx eslint .  -> Nöqtə (.) bütün cari qovluqdakı faylları yoxlayır.
npx eslint src/index.js -> İstəyə görə bir fayl da göstərə bilərsiniz, məsələn: src/index.js bu fayl yoxlanilsin

# package.json daxilində skript əlavə etmək: ("lint": "eslint .")
package.json faylında "scripts" bölməsinə əlavə edirik: "lint": "eslint ." -> İndi komandada yazanda npm run lint bütün layihəni yoxlayacaq.
npm run lint | bun run lint 

* eger lint scriptini istifade etseniz => bun run lint , npm run lint -> bu zaman butun fayllar yoxlanilacq
* xususi fayllar npx ile calisdirin -> npx eslint src/index.js

# Xüsusi qovluqları ESLint-in yoxlamamasını istəyirsinizsə, .eslintignore faylı yaradılır:
Məsələn, node_modules/ qovluğunu və ya dist/ kimi build qovluqlarını oraya yazırsınız.

# ESLint-in avtomatik səhvləri düzəltməsi: (npx eslint . --fix)
npx eslint . --fix => Nöqtə (.) bütün cari qovluqdakı fayllararda avtomatik səhvləri düzəldir.
npx eslint src/index.js --fix =>   İstəyə görə bir faylda da avtomatik səhvlər düzəldsin., məsələn: src/index.js bu faylda duzelt

# ESLint-in avtomatik səhvləri düzəltməsi package.json daxilində əlavə edə bilərsiniz (scripts hissesine)
"lint:fix": "eslint . --fix"
* eger lint:fix scriptini istifade etseniz => bun run lint:fix , npm run lint:fix -> bu zaman butun fayllar yoxlanilacq
* xususi fayllar npx ile calisdirin -> npx eslint src/index.js --fix

# VSCode-da ESLint istifadəsi
VSCode üçün ESLint plugin (extension) yükləmək lazımdır.
settings.json-da aşağıdakı seti əlavə edin ki, kodu saxlayanda ESLint avtomatik səhvləri tapsın və düzəltsin:
"editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
}


Prettier nədir?
Prettier — kodun avtomatik formatlanması üçün istifadə olunan alətdir.
Kodun görünüşünü (indentasiya, vergül, boşluq və s.) standartlaşdırır.
Kodun oxunaqlı və vahid görünməsini təmin edir.

# Prettier qurulması
npm install --save-dev --save-exact prettier  
bun, yarn, pnpm ve sair istifade ede bilersiz ex: bun add  --save-dev --save-exact prettier

# Boş .prettierrc konfiqurasiya faylı yaradılır ki, alət aktiv olsun:
node --eval "fs.writeFileSync('.prettierrc','{}\n')"  -> bu scripti terminalda calisdirmaq lazimdir

# Hər hansı qovluq və faylları formatlamamağa .prettierignore faylında göstərə bilərsiniz.
build 
node_modules
coverage

# Faylları formatlamaq:(npx prettier . --write)
Bütün faylları formatlamaq üçün: npx prettier . --write
xususi fayllar formatlamaq üçün: npx prettier src/index.js --write

# Formatın düzgün olub olmadığını yoxlamaq üçün:
Bütün fayl:  npx prettier . --check
xususi fayl: npx prettier  src/index.js --check

# Prettier və ESLint birlikdə necə işləyir?(eslint-config-prettier, eslint-plugin-prettier)
ESLint və Prettier bəzən bir-biri ilə konflikt yaradır, çünki ikisi də kodu formatlamağa çalışır.
eslint-config-prettier => Bu paket konfliktləri önləmək üçün istifadə edilir.
eslint-config-prettier => Bu paket ESLint-in formatlama ilə bağlı qaydalarını deaktiv edir, beləliklə Prettier formatlamanı tam nəzarət edir.
eslint-plugin-prettier => isə Prettier-in ESLint daxilində işləməsini təmin edir.

# VSCode üçün Prettier plugin => Prettier VSCode genişləməsini yükləyin. settings.json faylında əlavə edin:
"editor.defaultFormatter": "esbenp.prettier-vscode",
"editor.formatOnSave": true -> husky ve lint-stage istifade edirsense false et 


🔧 1. eslint-config-prettier nədir?
Məqsədi:
Bu konfiqurasiya faylı ESLint-in Prettier ilə ziddiyyət təşkil edən qaydalarını deaktiv edir.

ESLint-in bəzi qaydaları Prettier-in etdiyi formatlamaya zidd ola bilər (məsələn: arrow-body-style, prefer-arrow-callback və s.).
eslint-config-prettier bu cür qaydaları "off" edərək Prettier-in yolunu açır.

🔧 2. eslint-plugin-prettier nədir?
Məqsədi:
Prettier-i plugin kimi ESLint-ə əlavə edir və formatlama səhvlərini ESLint səhvi kimi göstərir.

Kod Prettier qaydalarına uyğun deyilsə, ESLint xəta kimi (red squiggles) göstərir.

eslint --fix ilə həm ESLint, həm də Prettier qaydaları ilə kod düzəldilir.
⚖️ Fərqlər
Paket	Məqsəd	Quraşdırılma Yeri	Nümunə
eslint-config-prettier	ESLint-in Prettier ilə zidd qaydalarını söndürür	extends içində	extends: ['prettier']
eslint-plugin-prettier	Prettier-in özünü ESLint plugin kimi işə salır	plugins və rules içində	rules: { 'prettier/prettier': 'error' }

* Əgər eslint-plugin-prettier istifadə edirsənsə, o artıq avtomatik eslint-config-prettier-i da daxil edir (recommended konfiqurasiyada).

# ESLint + Prettier quraşdırmaq üçün (https://www.npmjs.com/package/eslint-config-prettier)
npm install --save-dev eslint-config-prettier eslint-plugin-prettier  (bun, yarn, pnpm de istifade ede bilersiz)
-----------------------------------------------------------------
// eslint.config.js
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';
import globals from 'globals';

/** @type {import('eslint').Linter.FlatConfig[]} */
export default [
  {
    files: ['**/*.js'],
    languageOptions: {
      globals: { ...globals.es2021 },
    },
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      'quotes': ['error', 'single'],
      // Prettier plugin qaydaları (səhvləri ESLint-də göstərmək üçün)
      ...prettierPlugin.configs.recommended.rules,
      // Prettier ilə ziddiyyət yaradan ESLint qaydalarını söndürmək üçün
      ...eslintConfigPrettier.rules
    },
  },
];
-------------------------------------------------------------------------------


# FlatCompat və ya FlatConfig?
FlatCompat ilə keçid (köhnə qaydaları çevirmək üçün)
ex
import { FlatCompat } from '@eslint/eslintrc';
const compat = new FlatCompat({ baseDirectory: __dirname });
...
...compat.extends("plugin:prettier/recommended")

2. Tam FlatConfig (seçdiyin üsul ✅)
Əlavə paketlərə ehtiyac yoxdur, sadəcə eslint-plugin-prettier, eslint-config-prettier-dən lazım olanları birbaşa qaydalara əlavə edirsən:
rules: {
  ...jsRules,
  ...prettierPlugin.configs.recommended.rules,
  ...eslintConfigPrettier.rules
}

Plugins necə əlavə edilir (FlatConfig ilə):
FlatConfig-də pluginlər aşağıdakı kimi əlavə olunur:
plugins: {
  prettier: prettierPlugin
}

sonda 
---------------------------------------------------------------------------------
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';
import typescriptPlugin from '@typescript-eslint/eslint-plugin';
import globals from 'globals';

const jsRules = {
  quotes: ['error', 'single', { avoidEscape: true }],
  'no-undef': 'warn',
  // Buraya öz qaydalarını əlavə edə bilərsən
};

/** @type {import('eslint').Linter.FlatConfig[]} */
export default [
  // JavaScript faylları üçün konfiqurasiya
  {
    files: ['**/*.{js,mjs,cjs}'],
    languageOptions: {
      globals: { ...globals.es2021 },
      parserOptions: { ecmaVersion: 2021, sourceType: 'module' },
    },
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      ...jsRules,
      ...prettierPlugin.configs.recommended.rules,  // prettier plugin qaydaları (prettier format səhvlərini göstərir)
      ...eslintConfigPrettier.rules,                // prettier ilə ziddiyyət yaradan qaydalar söndürülür
    },
  },

  // TypeScript faylları üçün konfiqurasiya
  {
    files: ['**/*.{ts,tsx}'],
    languageOptions: {
      globals: { ...globals.es2021 },
      parser: '@typescript-eslint/parser',
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
        project: './tsconfig.json',  // Əgər varsa
      },
    },
    plugins: {
      prettier: prettierPlugin,
      '@typescript-eslint': typescriptPlugin,
    },
    rules: {
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
      '@typescript-eslint/explicit-function-return-type': 'warn',
      '@typescript-eslint/no-explicit-any': 'off',
      // Öz typescript qaydaların buraya
    },
  },

  // JSON və JSONC faylları üçün (optional)
  {
    files: ['**/*.json', '**/*.jsonc'],
    languageOptions: {
      parser: 'jsonc-eslint-parser',
    },
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
  },
];
--------------------------------------------------------------------------


3. Qısa açıqlama
JavaScript blokunda prettierPlugin.configs.recommended.rules Prettier qaydalarını ESLint-in qaydalarına əlavə edir, yəni Prettier formatlama səhvlərini ESLint ilə görürsən.

eslintConfigPrettier.rules isə Prettier ilə ziddiyyət yaradan ESLint qaydalarını söndürür.

TypeScript üçün @typescript-eslint/parser istifadə edilir və əlavə plugin yüklənir.

JSON üçün jsonc-eslint-parser istifadə oluna bilər.

Qaydaları və pluginləri lazımi fayl növlərinə görə granular (hissə-hissə) tətbiq edirik.

4. İndi sadəcə
eslint --fix ilə həm kodun lint səhvlərini, həm də formatlama qaydalarını tək bir yerdə həll edə bilərsən.

VSCode ESLint plugin ilə də dərhal qırmızı xətlərlə xəbərdarlıq alırsan.


# React üçün ESLint + Prettier (Flat Config nümunəsi)
---------------------------------------------------------------------------------------
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';
import reactPlugin from 'eslint-plugin-react';
import reactHooksPlugin from 'eslint-plugin-react-hooks';
import typescriptPlugin from '@typescript-eslint/eslint-plugin';
import globals from 'globals';

const commonRules = {
  quotes: ['error', 'single', { avoidEscape: true }],
  'no-undef': 'warn',
  // Buraya ümumi qaydalarını əlavə et
};

/** @type {import('eslint').Linter.FlatConfig[]} */
export default [
  // React TSX/JSX faylları üçün
  {
    files: ['**/*.{jsx,tsx}'],
    languageOptions: {
      globals: { ...globals.es2021, React: 'writable' },
      parser: '@typescript-eslint/parser',
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
        ecmaFeatures: {
          jsx: true,
        },
        project: './tsconfig.json', // varsa
      },
    },
    plugins: {
      prettier: prettierPlugin,
      react: reactPlugin,
      'react-hooks': reactHooksPlugin,
      '@typescript-eslint': typescriptPlugin,
    },
    rules: {
      ...commonRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
      // React plugin qaydaları
      'react/react-in-jsx-scope': 'off', // React 17+ üçün lazım deyil
      'react/jsx-uses-react': 'off',     // React 17+ üçün lazım deyil
      'react/jsx-uses-vars': 'error',
      'react-hooks/rules-of-hooks': 'error',
      'react-hooks/exhaustive-deps': 'warn',
      // Typescript qaydaları
      '@typescript-eslint/explicit-function-return-type': 'warn',
      '@typescript-eslint/no-explicit-any': 'off',
      // Əlavə qaydalar əlavə oluna bilər
    },
    settings: {
      react: {
        version: 'detect', // React versiyasını avtomatik tapır
      },
    },
  },
];
---------------------------------------------------------------------------------------

# Qısa açıqlama:
files - JSX və TSX fayllarını əhatə edir.
parser - @typescript-eslint/parser olaraq təyin edilib, Typescript və JSX oxumaq üçün.
plugins - Prettier, React, React Hooks və TypeScript pluginləri əlavə olunub.
rules -
Ümumi, Prettier qaydaları və ESLint-Prettier konfliktlərini deaktiv edən qaydalar yüklənib.
React və React Hooks üçün spesifik qaydalar əlavə olunub.
settings.react.version - React versiyasını avtomatik tapır ki, əlavə konfiqurasiya lazım olmasın.

# Növbəti addımlar
VSCode ESLint və Prettier extension-larını aktivləşdir.
Kodunu saxlayanda avtomatik lint və formatlama işləsin.
eslint --fix əmrini işə salaraq həm lint, həm formatlama səhvlərini düzəlt.


# Jest test faylları üçün ESLint + Prettier (Flat Config nümunəsi)
---------------------------------------------------------------------------------------
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';
import jestPlugin from 'eslint-plugin-jest';
import globals from 'globals';

const testRules = {
  'jest/no-disabled-tests': 'warn',
  'jest/no-focused-tests': 'error',
  'jest/no-identical-title': 'error',
  'jest/prefer-to-have-length': 'warn',
  'jest/valid-expect': 'error',
  // əlavə jest qaydaları əlavə oluna bilər
};

/** @type {import('eslint').Linter.FlatConfig[]} */
export default [
  {
    files: ['**/*.test.js', '**/*.test.ts', '**/*.spec.js', '**/*.spec.ts'],
    languageOptions: {
      globals: { ...globals.jest, ...globals.es2021 },
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
      },
    },
    plugins: {
      prettier: prettierPlugin,
      jest: jestPlugin,
    },
    rules: {
      ...testRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
  },
];
---------------------------------------------------------------------------------------

# Node.js üçün ESLint + Prettier (Flat Config nümunəsi)
---------------------------------------------------------------------------------------
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';
import globals from 'globals';

const nodeRules = {
  'no-console': 'off', // Konsol loglarını backenddə qəbul edirik
  'no-unused-vars': 'warn',
  'no-process-exit': 'off',
  // Öz qaydalarını əlavə edə bilərsən
};

/** @type {import('eslint').Linter.FlatConfig[]} */
export default [
  {
    files: ['**/*.js', '**/*.cjs'],
    languageOptions: {
      globals: { ...globals.node, ...globals.es2021 },
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
      },
      env: {
        node: true,
        es2021: true,
      },
    },
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      ...nodeRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
  },
];
---------------------------------------------------------------------------------------

# Express.js üçün ESLint + Prettier Flat Config nümunəsi

import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';
import globals from 'globals';

const expressRules = {
  'no-console': 'off',               // Konsol loglarına icazə veririk
  'no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],  // İstifadə olunmayan parametrlər üçün xəbərdarlıq, _ ilə başlayanlar nəzərə alınmasın
  'no-underscore-dangle': 'off',    // Express-də bəzən _ ilə başlayan dəyişənlər olur
  'consistent-return': 'error',     // Funksiyalar ya həmişə return etməlidir, ya etməməlidir
  'no-param-reassign': ['error', { props: false }],  // Parametrlərin dəyişdirilməsinə müəyyən qədər icazə verilir
  'callback-return': 'error',       // Callback funksiyalarından sonra return olmalıdır
  'no-magic-numbers': ['warn', { ignore: [0, 1] }], // Sihirli ədədlərdən çəkin, amma 0 və 1-ə icazə var
  // Daha çox öz qaydalarını əlavə edə bilərsən
};

/** @type {import('eslint').Linter.FlatConfig[]} */
export default [
  {
    files: ['**/*.js', '**/*.cjs'],
    languageOptions: {
      globals: { ...globals.node, ...globals.es2021 },
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
      },
      env: {
        node: true,
        es2021: true,
      },
    },
    plugins: {
      prettier: prettierPlugin,
    },
    rules: {
      ...expressRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
  },
];

# sonda
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';

import reactPlugin from 'eslint-plugin-react';
import reactHooksPlugin from 'eslint-plugin-react-hooks';

import typescriptPlugin from '@typescript-eslint/eslint-plugin';

import globals from 'globals';

const commonRules = {
  quotes: ['error', 'single', { avoidEscape: true }],
  'no-console': 'warn',
  'no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],
  'no-underscore-dangle': 'off',
  'consistent-return': 'error',
};

const backendRules = {
  ...commonRules,
  'no-console': 'off', // Backenddə konsola icazə var
  'no-param-reassign': ['error', { props: false }],
  'callback-return': 'error',
};

const reactRules = {
  ...commonRules,
  'react/react-in-jsx-scope': 'off', // React 17+ üçün
  'react/jsx-uses-react': 'off',     // React 17+ üçün
  'react/jsx-uses-vars': 'error',
  'react-hooks/rules-of-hooks': 'error',
  'react-hooks/exhaustive-deps': 'warn',
};

const tsRules = {
  '@typescript-eslint/explicit-function-return-type': 'warn',
  '@typescript-eslint/no-explicit-any': 'off',
};

export default [
  // Backend JS
  {
    files: ['**/*.js', '**/*.cjs'],
    languageOptions: {
      globals: { ...globals.node, ...globals.es2021 },
      parserOptions: { ecmaVersion: 2021, sourceType: 'module' },
      env: { node: true, es2021: true },
    },
    plugins: { prettier: prettierPlugin },
    rules: {
      ...backendRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
  },

  // React + TSX / JSX + TS faylları
  {
    files: ['**/*.{jsx,tsx}'],
    languageOptions: {
      globals: { ...globals.es2021, React: 'writable' },
      parser: '@typescript-eslint/parser',
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
        ecmaFeatures: { jsx: true },
        project: './tsconfig.json', // varsa
      },
    },
    plugins: {
      prettier: prettierPlugin,
      react: reactPlugin,
      'react-hooks': reactHooksPlugin,
      '@typescript-eslint': typescriptPlugin,
    },
    rules: {
      ...reactRules,
      ...tsRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
    settings: { react: { version: 'detect' } },
  },

  // TypeScript (.ts) faylları üçün ayrıca blok
  {
    files: ['**/*.ts'],
    languageOptions: {
      globals: { ...globals.es2021 },
      parser: '@typescript-eslint/parser',
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
        project: './tsconfig.json', // varsa
      },
    },
    plugins: {
      prettier: prettierPlugin,
      '@typescript-eslint': typescriptPlugin,
    },
    rules: {
      ...commonRules,
      ...tsRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
  },
];

eslint.config.js faylı olaraq yadda saxla.
VSCode ESLint və Prettier pluginlərini aktivləşdir.
eslint --fix ilə kodun formatlanması və lint səhvlərinin düzəlməsini təmin et.
Lazım gəldikcə qaydaları dəyişdir, əlavə et.

----------------------------------------------------------HUSKY-------------------------------------------------------------------------------
# Husky ilə ESLint + Prettier pre-commit hook qurulması
1. Husky və lint-staged quraşdırılması => npm install --save-dev husky lint-staged
2. Husky aktivləşdirilməsi => npx husky install  -> Bu əmrlə .husky qovluğu yaranacaq.
3. package.json-a aşağıdakı sətri əlavə et:
4. {
  "scripts": {
    "prepare": "husky install"
  }
}
Bu npm install sonrası avtomatik husky aktivləşməsini təmin edir.

5. Pre-commit hook yaratmaq => npx husky add .husky/pre-commit "npx lint-staged"
6. package.json-a lint-staged konfiqurasiyasını əlavə et:
{
  "lint-staged": {
    "*.{js,jsx,ts,tsx}": [
      "eslint --fix",
      "prettier --write",
      "git add"
    ]
  }
}

#  İndi nə baş verir?
Git-ə faylları git add etdikdə, 
pre-commit hook işə düşür, 
lint-staged dəyişən fayllarda ESLint və Prettier-ni avtomatik işlədir,
Dəyişiklikləri avtomatik düzəldir və git add ilə yenidən əlavə edir,
Beləcə format və lint qaydalarına uyğun olmayan kodlar commit edilmədən əvvəl düzəlir.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
1. eslint.config.js
import prettierPlugin from 'eslint-plugin-prettier';
import eslintConfigPrettier from 'eslint-config-prettier';

import reactPlugin from 'eslint-plugin-react';
import reactHooksPlugin from 'eslint-plugin-react-hooks';

import typescriptPlugin from '@typescript-eslint/eslint-plugin';

import globals from 'globals';

const commonRules = {
  quotes: ['error', 'single', { avoidEscape: true }],
  'no-console': 'warn',
  'no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],
  'no-underscore-dangle': 'off',
  'consistent-return': 'error',
};

const reactRules = {
  ...commonRules,
  'react/react-in-jsx-scope': 'off', // React 17+ və Next.js-də lazım deyil
  'react/jsx-uses-react': 'off',     // React 17+ və Next.js-də lazım deyil
  'react/jsx-uses-vars': 'error',
  'react-hooks/rules-of-hooks': 'error',
  'react-hooks/exhaustive-deps': 'warn',
};

const tsRules = {
  '@typescript-eslint/explicit-function-return-type': 'warn',
  '@typescript-eslint/no-explicit-any': 'off',
};

export default [
  // React + Next.js + TSX/JSX faylları
  {
    files: ['**/*.{tsx,jsx}'],
    languageOptions: {
      globals: { ...globals.es2021, React: 'writable' },
      parser: '@typescript-eslint/parser',
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
        ecmaFeatures: { jsx: true },
        project: ['./tsconfig.json'], // varsa
      },
    },
    plugins: {
      prettier: prettierPlugin,
      react: reactPlugin,
      'react-hooks': reactHooksPlugin,
      '@typescript-eslint': typescriptPlugin,
    },
    rules: {
      ...reactRules,
      ...tsRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
    settings: { react: { version: 'detect' } },
  },

  // TypeScript (.ts) faylları üçün ayrıca blok
  {
    files: ['**/*.ts'],
    languageOptions: {
      globals: { ...globals.es2021 },
      parser: '@typescript-eslint/parser',
      parserOptions: {
        ecmaVersion: 2021,
        sourceType: 'module',
        project: ['./tsconfig.json'], // varsa
      },
    },
    plugins: {
      prettier: prettierPlugin,
      '@typescript-eslint': typescriptPlugin,
    },
    rules: {
      ...commonRules,
      ...tsRules,
      ...prettierPlugin.configs.recommended.rules,
      ...eslintConfigPrettier.rules,
    },
  },
];


2. package.json — Husky və lint-staged konfiqurasiyası
{
  "scripts": {
    "prepare": "husky install"
  },
  "lint-staged": {
    "*.{ts,tsx,js,jsx}": [
      "eslint --fix",
      "prettier --write",
      "git add"
    ]
  },
  "devDependencies": {
    "eslint": "^8.x.x",
    "eslint-config-prettier": "^9.x.x",
    "eslint-plugin-prettier": "^4.x.x",
    "eslint-plugin-react": "^7.x.x",
    "eslint-plugin-react-hooks": "^4.x.x",
    "@typescript-eslint/eslint-plugin": "^6.x.x",
    "@typescript-eslint/parser": "^6.x.x",
    "globals": "^15.x.x",
    "husky": "^8.x.x",
    "lint-staged": "^14.x.x",
    "prettier": "^3.x.x"
  }
}


3. .husky/pre-commit faylı (avtomatik yaradılır, amma yoxla)
#!/bin/sh
. "$(dirname "$0")/_/husky.sh"

npx lint-staged


4. Quraşdırma və işə salma addımları
npm install
npx husky install
npm run prepare
npx husky add .husky/pre-commit "npx lint-staged"

Git commit etmədən öncə lint-staged dəyişmiş fayllarda eslint --fix və prettier --write işlədəcək.
Kod avtomatik düzələcək və commit ediləcək.
VSCode və digər IDE-lərdə də eyni qaydalar tətbiq olunacaq.




----------------------------------------------------------------------Husky-----------------------------------------------------------------------
Husky və lint-staged nədir?
Husky — Git commit əmrlərindən əvvəl avtomatik skriptlər işlətmək üçün alətdir (məsələn, lint yoxlaması).
lint-staged — yalnız commit olunan fayllara lint tətbiq etmək üçündür.

# Husky və lint-staged quraşdırılması
npm install --save-dev husky lint-staged
npx husky install
npx husky add .husky/pre-commit "npx lint-staged"

# package.json-a əlavə edin:
"lint-staged": {
  "*.{js,ts,jsx,tsx}": [
    "eslint --fix",
    "prettier --write"
  ]
}

İndi commit edərkən avtomatik lint və format yoxlaması işləyəcək.

-------------------------------------------------------------Stylelint-----------------------------------------------------------------------
Stylelint nədir?
Stylelint — CSS və SCSS kimi stil fayllarının keyfiyyətini yoxlamaq üçün lint alətidir.
Kodda səhvləri tapır və xəbərdarlıq edir.

# Stylelint quraşdırılması:(npm init stylelint --save-dev)
2. İstəyə görə .stylelintrc faylını konfiqurasiya edin.
3. package.json-a skript əlavə edin:(skripts e)
"stylelint": "stylelint 'src/**/*.{css,scss}'",
"stylelint:fix": "stylelint 'src/**/*.{css,scss}' --fix"

# VSCode üçün Stylelint extension yükləyin ki, kodda səhvlər görünsün.
Nəticə
ESLint — JavaScript/TypeScript koduna baxır, səhvləri tapır.
Prettier — kodu avtomatik gözəl formatlayır.
eslint-config-prettier — konfliktlərin qarşısını alır.
Husky + lint-staged — Git commit-dən əvvəl avtomatik yoxlamalar edir.
Stylelint — CSS və SCSS üçün lint.


 
































