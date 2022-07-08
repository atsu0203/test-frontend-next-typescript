## 1. Nextjs Project 新規作成
### 1-1. yarn install *インストールしていない場合
    npm install --global yarn
    yarn --version
### 1-2.  create-next-app
    npx create-next-app .
#### Node.js version 10.13以降が必要です。 -> ターミナル `node -v`でver確認出来ます。
### 1-3.  React-Testing-Libraryのインストール
    yarn add -D jest@27.5.1 @testing-library/react @testing-library/jest-dom jest-css-modules
### 1-4.  Project folder 直下に"jest.config.js"ファイルを作成して下記設定を追加
    touch jest.config.js
~~~
const nextJest = require('next/jest')
const createJestConfig = nextJest({
  dir: './',
})
const customJestConfig = {
  moduleDirectories: ['node_modules', '<rootDir>/'],
  testEnvironment: 'jest-environment-jsdom',
}
module.exports = createJestConfig(customJestConfig)
~~~
### ~~1-5.  package.json に jest の設定を追記~~
### 1-6.  package.jsonに test scriptを追記
~~~
    "scripts": {
        ...
        "test": "jest --watch"
    },
~~~
### 1-7.  prettierの設定 : settingsでRequire Config + Format On Saveにチェック
    touch .prettierrc
~~~
    {
        "singleQuote": true,
        "semi": false
    }
~~~  
## 2. Test動作確認
### 2-1. `__tests__`フォルダと`Home.test.tsx`ファイルの作成
~~~
import { render, screen } from '@testing-library/react'
import '@testing-library/jest-dom/extend-expect'
import Home from '../pages/index'
it('Should render title text', () => {
  render(<Home />)
  expect(screen.getByText('Next.js!')).toBeInTheDocument()
})
~~~
### 2-2. yarn test -> テストがPASSするか確認
~~~
 PASS  __tests__/Home.test.tsx
  ✓ Should render hello text (20 ms)
Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        1.728 s, estimated 2 s
~~~
















This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.ts`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
