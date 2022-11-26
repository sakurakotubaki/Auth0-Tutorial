# Auth0をReactで使う
公式チュートリアルを参考に進めた
今回はViteを使用しているので、create react appとは設定の仕方が違って、
ハマった!
通常のcreate react appだとhttp://localhost:3000で設定できる!

```
http://は、Viteのhttpを指定する
# こちらを指定する
http://127.0.0.1:5173/
```

こちらのコマンドでReactプロジェクトを作成する
```
npm create vite@latest
```
---------

プロジェクトを作成したら、componentsディレクトリを作成して、認証に必要なコンポーネントを作成する

## 認証用のコンポーネント
- ログインボタン
- ログアウトボタン
- プロフィール表示コンポーネント

------

.envファイルを作成して、環境変数を作成する。Viteだと設定の仕方が違うので、注意が必要!<br>
.envは.gitignoreでGitのコミットの対象から外しておく。

.env
```
VITE_AUTH0_DOMAIN=********.com
VITE_AUTH0_CLIENT_ID=*********SWMAEj
```

main.jsxにAuth0の設定をしているコードがありこちらで、ドメインとクライアントIDを使用する。
```jsx
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import { Auth0Provider } from "@auth0/auth0-react";
const domain = import.meta.env.VITE_AUTH0_DOMAIN;
const client = import.meta.env.VITE_AUTH0_CLIENT_ID;

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <Auth0Provider
    domain={domain}
    clientId={client}
    redirectUri={window.location.origin}
  >
    <App />
  </Auth0Provider>
  </React.StrictMode>
)
```
