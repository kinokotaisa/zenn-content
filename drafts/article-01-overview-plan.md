# 第一弾記事 執筆プラン：ワカバーランド全体像（序章）

> このファイルはメインPC（Windows）とサブMacで Claude Code の認識を揃えるための「正本」。
> 記事の方針が変わったらここを更新する（machine-local なメモリではなくリポジトリで一元管理）。
> 状態: 📝 執筆中（本文ドラフト完成・全5章＋つかみ → プレビュー/推敲へ）／最終更新: 2026-06-11

---

## 決定事項

- **第一弾記事**：ワカバーランド全体像（序章）
- **公開先**：Zenn（この `zenn-content` リポジトリ、GitHub連携による push→自動公開）
- **タイミング**：v0.1.0完成後の今（2026-06-10〜）に着手。構成確定済み・本文ドラフトから

## 確定事項（2026-06-11・本文ドラフト完成）

- **タイトル（確定）**：スマホのタップで「正拳突き人形」が正拳を繰り出すまで
  - slug `seiken-overview` / emoji 🥋 / type tech / `published: false`（記事ファイル: `articles/seiken-overview.md`）
- **文体スタンス（確定）**：ハイブリッド＝地の文は端正なデスマス調（高飛車にせず親しみ重視）。つかみ・実例の決め所など"見せ場"だけ温度を上げる。情景・デモの実況は常体、読者への説明は敬体。にぎやかさは写真・デバイス名・絵文字に担わせ、文章は静かに保ち、その**ギャップ自体を売り**にする
- **「ワカバーランド」**：記事中では未定義のブランド名を出さない（「このプロジェクト／この連載」で通す）。将来ブランド化するなら、一度ちゃんと名前を紹介してから使う
- **表現**：「殴る」は不使用（「正拳を繰り出す／パンチ」で統一）
- **つかみ**：デモ先行（スマホ→離れた人形が正拳→カウント+1、v0.1.0で実機実証済みを起点に）
- **3章の深さ**：概要レベル（HW→FW→SW→NW＋全体図。深掘りは第二弾へ）。★ハイライト＝「圧力センサと同じ端子にLOWパルス→FW無改造で遠隔化」
- **計数**：遠隔モードはセンサーでなくラズパイのカメラ＋OpenCVで画像認識
- **チャネル分割**：🎬ショート動画＝完成デモ／📝Zenn＝裏側（HW〜NWのつなぎ目）
- **連載構成**：序章のあとは別途練り直す（#5/gunicorn/実機常駐の濃い話は第二弾「Step 0開発記」へ温存）

## 執筆方針

- 「HW・FW・SW・NW をつなぐ」というプロジェクトの主題を宣言する序章として位置づける
- 今後の Step 0〜4 記事・デバイス記事すべてのハブ（入口・目次）になる
- **「プロジェクト紹介ポエム」にしない**ために、**正拳突き人形を縦串の実例**にする
  - 1台のおもちゃが動くまでに HW→FW→SW→NW がどう連鎖するかを具体的に辿る
  - これにより「紹介」が「実例解説」になる

## 見出し構成（確定・本文の実見出し）

- （つかみ・見出しなし／デモ先行）
1. ## なぜ作っているのか（身近/壮大なシステムへの好奇心 → 作りながら一緒に学ぶ・想定読者）
2. ## このプロジェクトの地図（身近なシステムの「形」→ 自分でつくる → その名もseikenシステム）
3. ## 【実例】正拳突き人形が動くまでを、縦に辿る ← **記事の背骨**
   - HW：ATtiny402・SG90サーボ×2・スライダクランク・圧力センサ・DFPlayer・単3×3=4.5V
   - FW：トリガー→音声→ワンツーパンチ×3（引き150°↔突き30°/1セット約2.4秒）
   - SW：Vue遠隔操作・正拳回数モニター・カメラ＋OpenCVで計数・Flask/SQLite記録
   - NW：ブラウザ→Nginx→Flask(Socket.IO)→RPi→GPIO→ATtiny。★同じ端子にLOWパルス＝FW無改造
4. ## これからの道のり（🌐土台3ステップ：ローカル完成→クラウド化→対応デバイス拡大／🤖デバイスのラインナップ）
5. ## どう読んでほしいか（読み方＝つまみ食いOK・一緒に辿る／チャネル分割）

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

1. `npx zenn preview` で表示確認（図はASCII仮置き → mermaid/画像へ差し替え）
2. 通し推敲（声に出して読む・冗長な所を削る）
3. デモ動画／スクショを用意し本文へ配置
4. `published: true` にして公開（push→自動公開）

## Zenn 執筆コマンド（クロスプラットフォーム）

リポジトリ直下で実行（パスは各マシンの `zenn-content` ルートに読み替え）。

```bash
# 初回のみ（node_modules は .gitignore 対象なので clone 後に必要）
npm install

# 記事ファイルは作成済み: articles/seiken-overview.md（published: false）
# プレビュー（http://localhost:8000）
npx zenn preview
```

> slug `seiken-overview` / emoji 🥋 / title 確定済み（記事ファイルに反映済み）。公開は `published: true` に変更して push。

---

## 将来の記事候補（第二弾以降）

- seiken Step 0 開発記（env化・認証・Redis・gevent移行）→ seiken 完成後に執筆
- 水やりぞうさん LCD ■表示トラブル（コントラスト ＋ SDA/SCL誤接続の合わせ技）→ 小ネタ・いつでも書ける
- 水やりぞうさん製作記（DFPlayer・リレー・防水処理などの知見大量）→ 単体完成後に
