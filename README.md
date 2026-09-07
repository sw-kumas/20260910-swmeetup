# AIがシニアエンジニアになったとき

社内向け・日本語・約10分のSlidev。全10枚（本編9枚＋参考資料）。
発表用メモは `slides.md` の各ページ末尾に記載。

```sh
pnpm install
pnpm dev
```

発表画面は <http://localhost:3030>、発表者画面は <http://localhost:3030/presenter>。
矢印キーで進行。9枚目の結論は3クリックで表示する。

```sh
pnpm build
```

## 画像3枚の差し替え

2枚目の `image-grid` にある3つの `image-placeholder` を画像に置き換える。
画像は `public/images/` に置き、例えば次のように参照する。

```html
<figure>
  <img src="/images/example-1.png" alt="検証動画で確認できる内容の説明">
  <figcaption><a href="実際の動画URL">動画名・投稿者</a></figcaption>
</figure>
```

同じ16:9の枠に、画像全体を切り取らずに収める。検証内容に合わせて発表用メモを調整し、参考資料ページにも動画の出典を追記する。現在は画像と動画の出典が未提供のため、差し替え枠だけを置いている。

## 内容と出典

`HANDOFF.md` は当初案。制作時は会話で合意した日本語の9枚構成を優先。
一次資料の確認結果は `MATT-RESPONSIBILITIES.md` に記録。
skillの引用は固定commitを参照し、原文と日本語の説明を区別している。
GPT-6の比較は検証動画を見た発表者の所感で、手順が能力を抑える因果関係を実証するものではない。
