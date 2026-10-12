# site/ — 公開用の静的ページ（利用規約・プライバシーポリシー・広告表記）

App Store 審査と AdMob に必要な、**外部から見られるURL**をここで用意する。
サーバー不要の静的HTMLなので、GitHub Pages（無料）に置く想定。

| ファイル | 用途 | アプリ側の参照先 |
|---|---|---|
| `index.html` | トップ（サポートURL。App Store Connect の「サポートURL」に使う） | — |
| `terms.html` | 利用規約 | `AppConfig.termsUrl` |
| `privacy.html` | プライバシーポリシー（App Store Connect の「プライバシーポリシーURL」にも使う） | `AppConfig.privacyPolicyUrl` |
| `ad-disclosure.html` | 広告・PR表記について（ステマ規制対応） | `AppConfig.adDisclosureUrl` |
| `app-ads.txt` | AdMob の認定販売者ファイル。**サイトのルート直下**に置く必要がある | AdMob 管理画面 |
| `style.css` | 共通スタイル（アプリと同じ紙色・インク色） | — |

## 公開前に差し替えるところ（黄色い枠 `.placeholder` の部分）

- `contact@example.com` → 問い合わせ専用のメールアドレス（本名・住所・電話番号は載せない）
- `2026年MM月DD日` → 公開日
- `index.html` の App Store リンク `id0000000000` → 審査通過後の本物のID
- `app-ads.txt` の `pub-0000000000000000` → AdMob の**サイト運営者ID**（AdMob 管理画面 › 設定 › アカウント情報）

## 公開手順（GitHub Pages）

GitHub の無料プランでは **Private リポジトリで Pages が使えない**ため、このフォルダだけを別の Public リポジトリにして公開する。

1. 公開用リポジトリ（例: `shigoto-animal-site`）を Public で作る
2. このフォルダの中身をそのリポジトリのルートに置いて push
3. Settings › Pages › Branch: `main` / `(root)` を選ぶ
4. 数分後 `https://<ユーザー名>.github.io/shigoto-animal-site/` で見られる
5. そのURLを `lib/core/config/app_config.dart` の `termsUrl` などに設定する
6. AdMob の「app-ads.txt」確認で `https://<ユーザー名>.github.io/shigoto-animal-site/app-ads.txt` が読めることを確認する
   - App Store Connect の「デベロッパWebサイト」欄に同じドメインを入れる（AdMob はストア掲載のURLを見に行く）

> 独自ドメインは必須ではない。ただし将来Web版の診断を出すなら、最初から独自ドメインにしておくとURLを変えずに済む。
