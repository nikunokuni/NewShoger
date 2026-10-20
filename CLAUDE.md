# NewShoger

全部のピンクのマスに移動しましょうゲーム。`index.html` 1ファイルで動く。

## 「みんなの問題」への追加

`puzzles.json` に入っている問題がアプリの「みんなの問題」に表示される。

ユーザーから共有URL (`...index.html#p=<コード>`) を渡されたら:

1. `#p=` の後ろを base64url デコードすると問題の JSON になる
   (`node -e 'console.log(Buffer.from(process.argv[1], "base64url").toString())' <コード>`)
2. その JSON を `puzzles.json` の配列の末尾に追加する。`name` は必要なら変える
3. コミットしてプッシュする

問題の形式:

```json
{
  "name": "問題名",
  "pieces": [[マス番号, "駒", "sente" | "gote", 成り 0 | 1]],
  "pink": [マス番号],
  "hands": { "sente": { "歩": 1 }, "gote": {} }
}
```

マス番号 = 段(0〜8, 上から) × 9 + 筋(0〜8, 左から)。
