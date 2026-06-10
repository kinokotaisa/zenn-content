# 第一弾記事 執筆プラン：ワカバーランド全体像（序章）

> このファイルはメインPC（Windows）とサブMacで Claude Code の認識を揃えるための「正本」。
> 記事の方針が変わったらここを更新する（machine-local なメモリではなくリポジトリで一元管理）。
> 状態: 📝 執筆中（構成確定済み・本文ドラフト着手前）／最終更新: 2026-06-10

---

## 決定事項

- **第一弾記事**：ワカバーランド全体像（序章）
- **公開先**：Zenn（この `zenn-content` リポジトリ、GitHub連携による push→自動公開）
- **タイミング**：v0.1.0完成後の今（2026-06-10〜）に着手。構成確定済み・本文ドラフトから

## 確定した方針（2026-06-10・B案＝共同アウトラインで決定）

- **つかみ**：デモ先行（スマホ→離れた人形が正拳→カウント+1、v0.1.0で実機実証済みを起点に）
- **3章の深さ**：概要レベル（HW→FW→SW→NW を各層1〜2文＋全体図1枚。深掘りは第二弾へ）
- **タイトル方向**：実例フック型A「スマホで“正拳突き人形”を殴らせるまで（ワカバーランド序章）」（語尾は微調整可）
- **序章のあとの連載構成は別途練り直す**（#5/gunicorn/実機常駐の濃い話は第二弾「Step 0開発記」へ温存）

## 執筆方針

- 「HW・FW・SW・NW をつなぐ」というプロジェクトの主題を宣言する序章として位置づける
- 今後の Step 0〜4 記事・デバイス記事すべてのハブ（入口・目次）になる
- **「プロジェクト紹介ポエム」にしない**ために、**正拳突き人形を縦串の実例**にする
  - 1台のおもちゃが動くまでに HW→FW→SW→NW がどう連鎖するかを具体的に辿る
  - これにより「紹介」が「実例解説」になる

## 見出し構成案（5本）

1. なぜ作っているのか（市販おもちゃを超える体験 ＋ 領域をまたぐ学び・想定読者）
2. ワカバーランドの地図（🌐 seikenプラットフォーム × 🤖 デバイスの2軸）
3. 【実例】正拳突き人形が動くまでを縦に辿る ← **記事の背骨**
   - HW：ATtiny402基板・サーボ・センサ
   - FW：トリガー検知と発声
   - SW：Webから遠隔操作・回数モニター
   - NW：ブラウザ→サーバー→RPi→人形 の通信経路
4. これからの道のり（この連載の目次：Step 0〜4 / デバイス展開）
5. どう読んでほしいか

---

## 素材の在りか（2026-06-10 確認済み・すべて dev/ 配下のGitHubリポジトリ）

各リポジトリは GitHub に push 済み。Mac では `git clone` / `git pull` で最新が揃う。

| 章 | 必要な素材 | 参照ファイル |
| :- | :--- | :--- |
| 1 なぜ作るか | プロジェクト方向性・想定読者 | `wakaba-land/README.md`・`wakaba-land/roadmap.md` |
| 2 地図（2軸） | seiken × デバイスの2軸構造 | `wakaba-land/README.md`・`wakaba-land/roadmap.md` |
| 3 HW | ATtiny402・サーボ・圧力センサ・BOM | `seiken-docs/seiken-doll/spec.md`（ハードウェア仕様）・`seiken-avr-firmware/README.md` |
| 3 FW | トリガー検知・発声 | `seiken-avr-firmware/seiken_gen2.ino`・`seiken-docs/seiken-doll/spec.md`（ファームウェア仕様） |
| 3 SW | Web遠隔操作・回数モニター | `seiken-docs/system-overview.md`・`seiken-docs/api-spec.md`・`seiken-docs/frontend.md` |
| 3 NW | ブラウザ→サーバー→RPi→人形 の経路 | `seiken-docs/system-overview.md`（2.1 全体アーキテクチャ）・`seiken-docs/rpi-client.md` |
| 4 道のり | Step 0〜4・デバイス展開 | `wakaba-land/roadmap.md` |
| 5 どう読むか | 本記事の位置づけ | 本ファイル（執筆方針） |

> 3章を本文化するときは HW/FW の数値・型番を `seiken-docs/seiken-doll/spec.md` と `seiken-avr-firmware/` で必ず事実確認する。

---

## 次の一手

1. Zenn で記事雛形を作成（下記コマンド）
2. 「0（つかみ／デモ先行）＋ 1章」から本文ドラフト
3. 3章の本文化時に HW/FW詳細を素材リポジトリで事実確認

## Zenn 執筆コマンド（クロスプラットフォーム）

リポジトリ直下で実行（パスは各マシンの `zenn-content` ルートに読み替え）。

```bash
# 初回のみ（node_modules は .gitignore 対象なので clone 後に必要）
npm install

# 記事雛形を作成
npx zenn new:article --slug overview-jo --title "スマホで正拳突き人形を殴らせるまで（ワカバーランド序章）" --type tech --emoji 🥋

# プレビュー（http://localhost:8000）
npx zenn preview
```

> slug・emoji は仮。確定時に上書きする。

---

## 将来の記事候補（第二弾以降）

- seiken Step 0 開発記（env化・認証・Redis・gevent移行）→ seiken 完成後に執筆
- 水やりぞうさん LCD ■表示トラブル（コントラスト ＋ SDA/SCL誤接続の合わせ技）→ 小ネタ・いつでも書ける
- 水やりぞうさん製作記（DFPlayer・リレー・防水処理などの知見大量）→ 単体完成後に
