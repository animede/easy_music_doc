# 第10章　完全ユーザーズマニュアル

> 本章では、Easy Musicの全画面要素・全設定項目を網羅的に解説します。各機能の詳細仕様、操作方法、制約事項を体系的にまとめたリファレンスマニュアルです。

---

## 10.1　画面構成

Easy Musicの画面は、上から順に以下の要素で構成されています。

```
┌─────────────────────────────────────────────┐
│  ヘッダー                                     │
│  ├ モード切替: カバー / リペイント / 自動演奏   │
│  └ 言語切替: JA ⇔ EN                         │
├─────────────────────────────────────────────┤
│  ジャンルグリッド（30タイル）                   │
│  ジャンルミックス（セカンダリジャンル選択）      │
├─────────────────────────────────────────────┤
│  おまかせ生成セクション                        │
│  ├ テキスト入力欄                             │
│  └ 🎲 ランダムボタン                          │
├─────────────────────────────────────────────┤
│  コントロールバー                              │
│  ├ 長さ / 言語 / 曲数 / モデル / 楽器のみ       │
├─────────────────────────────────────────────┤
│  ⚙ 詳細設定（アコーディオン）                  │
│  ├ STEP / Shift / Sampler / キャプション自動   │
│  └ Thinking                                   │
├─────────────────────────────────────────────┤
│  ✍ 作詞設定（アコーディオン）                  │
│  ├ ムードチップ（10種） / ボーカルチップ（6種）  │
│  ├ テーマ入力 / 歌詞入力                       │
│  └ ネガティブプロンプト                        │
├─────────────────────────────────────────────┤
│  🎵 音楽を生成 ボタン                          │
│  プログレスバー / ステータスメッセージ          │
├─────────────────────────────────────────────┤
│  インラインプレーヤー                          │
│  ├ トラック切替 / シークバー / 音量              │
│  └ ビジュアライザーオーバーレイ                  │
├─────────────────────────────────────────────┤
│  デバッグパネル（折りたたみ）                   │
├─────────────────────────────────────────────┤
│  生成履歴（折りたたみ）                        │
└─────────────────────────────────────────────┘
```

### モード別表示切替

通常モード、カバーモード、リペイントモード、JUKEBOXモードで表示される要素が異なります。

| 要素 | 通常 | カバー | リペイント | JUKEBOX |
|------|------|--------|---------|---------|
| ジャンルグリッド | ✅ | ❌ | ❌ | ✅（複数選択） |
| おまかせ生成 | ✅ | ❌ | ❌ | ❌ |
| コントロールバー | ✅ | 一部 | 一部 | ❌ |
| 作詞設定 | ✅ | 歌詞のみ | 歌詞のみ | ❌ |
| カバーパネル | ❌ | ✅ | ❌ | ❌ |
| リペイントパネル | ❌ | ❌ | ✅ | ❌ |
| JUKEBOXコントロール | ❌ | ❌ | ❌ | ✅ |

---

## 10.2　ジャンル選択（30ジャンル詳解）

ジャンルグリッドには30個のタイルが配置されています。各タイルには **キャプションヒント**（`data-caption-hint`）が埋め込まれており、選択時にこのヒントがキャプション生成の基礎となります。

### 洋楽メジャー（8ジャンル）

| ジャンル | キャプションヒント | 特徴 |
|---------|-------------------|------|
| **J-POP** | `J-POP, Japanese pop, catchy melody, bright, emotional vocal, polished production` | 日本のポップス。キャッチーなメロディと感情的なボーカル |
| **Rock** | `Rock, guitar-driven, energetic, powerful` | ギター主体のロック |
| **Jazz** | `Jazz, smooth, improvisational, sophisticated` | スムースジャズ、即興的 |
| **Electronic** | `Electronic, synth, dance, digital` | シンセサイザー主体の電子音楽 |
| **R&B** | `R&B, soulful, smooth, groove` | ソウルフルなリズム＆ブルース |
| **Hip-Hop** | `Hip-Hop, rhythmic, rap, beats` | ラップ、ビート重視 |
| **Country** | `Country music, acoustic guitar, banjo, fiddle, steel guitar, warm storytelling vocals, heartfelt and honest, Nashville sound` | カントリーミュージック。アコースティックギター、バンジョー、フィドル |
| **Folk** | `Folk, acoustic, warm, storytelling` | フォーク。アコースティック、ストーリーテリング |

### 年代系（4ジャンル）

| ジャンル | キャプションヒント | 特徴 |
|---------|-------------------|------|
| **70年代歌謡曲** | `1970s Japanese Kayokyoku, retro, nostalgic, analog, dramatic vocal, orchestral arrangement` | レトロ、オーケストラアレンジ |
| **80年代フォーク** | `1980s Japanese folk pop, acoustic guitar, warm analog recording, singer-songwriter, poetic, nostalgic` | シンガーソングライター、詩的 |
| **90年代J-POP** | `1990s J-POP, bright, emotional, catchy melody, band sound, Japanese pop golden era` | J-POP黄金期、バンドサウンド |
| **ニューミュージック** | `Japanese New Music, singer-songwriter, poetic, mellow, 1970s-1980s acoustic pop` | 1970〜80年代のアコースティックポップ |

### 日本特化（5ジャンル）

| ジャンル | キャプションヒント | 特徴 |
|---------|-------------------|------|
| **ボカロ** | `Vocaloid, synthetic voice, electronic, fast tempo, digital, futuristic Japanese pop` | シンセティックな声、高速テンポ |
| **アニソン** | `Anime song, dramatic, energetic, emotional, opening theme, Japanese anime soundtrack` | ドラマティック、アニメOP風 |
| **童謡** | `Japanese children's song, gentle, simple, warm, nursery rhyme, innocent, acoustic` | 優しく温かい子供向けの歌 |
| **演歌** | `Enka, traditional Japanese ballad, melancholic, vibrato, emotional, shamisen, koto` | こぶし、三味線、琴 |
| **民謡** | `Japanese Min'yo folk song, traditional, regional, shakuhachi, taiko, pentatonic scale` | 尺八、太鼓、ペンタトニック |

### ムード系（7ジャンル）

| ジャンル | キャプションヒント | インスト固定 |
|---------|-------------------|-------------|
| **Trance** | `Trance, purely instrumental, uplifting synth pads, euphoric build-ups and breakdowns, driving bassline, arpeggiated leads, 138 BPM, ethereal atmosphere, soaring melodies, no vocals` | ✅ |
| **ムード** | `Mood lounge music, purely instrumental, smooth jazz with mellow saxophone, warm electric piano chords, subtle brushed drums and walking bass, romantic and sophisticated, late night ambiance, medium slow tempo, polished production, no vocals` | ✅ |
| **ドライビング** | `Refreshing driving music, purely instrumental, bright acoustic guitar and clean electric guitar, light upbeat drums, moderate tempo around 110 BPM, warm bass, breezy and uplifting, coastal highway sunshine, open windows breeze, no vocals` | ✅ |
| **Acoustic Pop** | `Acoustic pop, warm fingerpicking acoustic guitar, gentle vocals, light percussion, simple and intimate arrangement, cafe atmosphere, singer-songwriter style` | ❌ |
| **ボサノバ** | `Bossa nova, Brazilian jazz, gentle acoustic guitar, soft percussion, warm, relaxed, cafe, sophisticated rhythm` | ❌ |
| **Lo-Fi** | `Lo-fi hip hop, chill beats, vinyl crackle, mellow piano, warm bass, relaxing, study music, nostalgic, tape saturation` | ❌ |
| **シティポップ** | `City pop, 1980s Japanese pop, funky bass, bright synth, groovy, urban, polished production, AOR influence, summer night` | ❌ |

### ワールド・ダンス（6ジャンル）

| ジャンル | キャプションヒント | インスト固定 |
|---------|-------------------|-------------|
| **シャンソン** | `French chanson, romantic, accordion musette, gentle acoustic guitar, expressive vocal with vibrato, Parisian cafe atmosphere, poetic lyrics, waltz rhythm, nostalgic European charm` | ❌ |
| **フォルクローレ** | `South American folklore, purely instrumental, Andean folk music, charango and quena flute melody, bombo drum and cajón percussion, warm acoustic guitar arpeggios, pentatonic scale, earthy and spiritual atmosphere, indigenous rhythm, no vocals` | ✅ |
| **レゲトン** | `Reggaeton, Latin urban dance, dembow rhythm, heavy 808 bass, snappy snare, reggaeton beat pattern, Spanish vocal style, party atmosphere, catchy hook, tropical club energy` | ❌ |
| **K-POP** | `K-POP, Korean pop, polished production, catchy hook, tight choreography beat, synth layers, powerful vocal, rap verse, dynamic arrangement, bright and energetic, modern dance pop` | ❌ |
| **Phonk** | `Phonk, Memphis rap influenced, dark cowbell pattern, distorted 808 bass, aggressive hi-hats, chopped vocal samples, drift car culture, hard-hitting drums, lo-fi gritty texture, high energy` | ❌ |
| **EDM** | `EDM, electronic dance music, massive synth drop, four-on-the-floor kick, sidechain compression, build-up and breakdown, festival anthem, euphoric lead synth, heavy sub bass, high energy crowd atmosphere` | ❌ |

> 💡 **インスト固定ジャンル**: Trance、ムード、ドライビング、フォルクローレの4ジャンルは `data-force-inst="true"` が設定されており、選択時に「楽器のみ」チェックが自動的にONになります。

---

## 10.3　ジャンルミックス

プライマリジャンルを選択した後、**「➕ ミックス：」** ドロップダウンでセカンダリジャンルを追加できます。

### 仕組み

1. プライマリジャンルのキャプションヒントを取得
2. セカンダリジャンルのキャプションヒントを取得
3. 2つのヒントを結合してキャプション生成の入力とする

### 効果的な組み合わせ例

| プライマリ | セカンダリ | 期待される効果 |
|-----------|----------|---------------|
| J-POP | Jazz | ジャジーなJ-POP |
| Rock | Electronic | エレクトロニックロック |
| 演歌 | Rock | ロック演歌 |
| Lo-Fi | Jazz | ジャズ寄りのLo-Fi |
| アニソン | EDM | EDMテイストのアニメソング |

> ⚠ ジャンルミックスは実験的な機能です。まったく異なるジャンルの組み合わせ（例: 民謡 + EDM）は予測不能な結果になることがあります。

---

## 10.4　コントロール設定詳解

### 長さ（Duration）

| 選択肢 | 値 | 説明 |
|--------|----|------|
| 自動（AI推定） | -1 | ACE-StepのLMが楽曲に適した長さを推定 |
| 30秒 | 30 | ショートクリップ |
| 45秒 | 45 | ショートバージョン |
| **60秒** | 60 | **デフォルト。標準的な長さ** |
| 90秒 | 90 | やや長め |
| 120秒 | 120 | フルコーラス程度 |
| 180秒 | 180 | 長めの楽曲 |
| 240秒 | 240 | 長尺曲 |
| 300秒 | 300 | 最大長（5分） |

> 💡 長い楽曲ほど生成時間も比例して増加します。プロトタイプ段階では60秒がおすすめです。

### 言語（Language）

ボーカルの言語を指定します。選択可能な言語:

| 言語 | コード | 説明 |
|------|--------|------|
| **日本語** | ja | デフォルト |
| 英語 | en | — |
| 中国語 | zh | — |
| 韓国語 | ko | — |
| スペイン語 | es | — |
| フランス語 | fr | — |
| ドイツ語 | de | — |
| イタリア語 | it | — |
| ポルトガル語 | pt | — |
| ロシア語 | ru | — |
| タイ語 | th | — |
| ベトナム語 | vi | — |
| インドネシア語 | id | — |

### 曲数（Batch Size）

| 選択肢 | 説明 |
|--------|------|
| **1曲** | デフォルト。1曲のみ生成 |
| 2曲 | 同じパラメータで2曲同時生成（異なるseed） |
| 4曲 | 同じパラメータで4曲同時生成（異なるseed） |

### モデル

| 選択肢 | 説明 |
|--------|------|
| **Turbo (高速)** | DMD蒸留済みモデル。8ステップで実用的品質。デフォルト |
| Base (高品質) | フルモデル。50ステップ以上推奨。高品質だが低速 |

### 楽器のみ（Instrumental）

チェックをONにすると、ボーカルなしのインストゥルメンタル楽曲が生成されます。インスト固定ジャンル（Trance/ムード/ドライビング/フォルクローレ）選択時は自動的にONになります。

---

## 10.5　詳細設定（Advanced Settings）

**「⚙ 詳細設定」** アコーディオンを展開すると表示されます。

### STEP（推論ステップ数）

| 値 | 説明 | 用途 |
|-----|------|------|
| **8** | Turbo推奨値。高速プロトタイプ | Turboモデルのデフォルト |
| 20 | 高速だが8より高品質 | バランス |
| 50 | 標準。Baseモデル推奨値 | 仕上げ段階 |
| 80 | 高品質 | 高品質な作品 |
| 100 | 最高品質。生成に数分 | 最終出力 |

### Shift（タイムステップシフト）

| 値 | 説明 |
|-----|------|
| **自動** | モデルに最適値を任せる（推奨） |
| 1.0 | ディテール重視。音色やニュアンスに注力 |
| 2.0 | バランス型 |
| 3.0 | Turbo推奨 |
| 4.0 | 構造重視 |
| 5.0 | 最大。楽曲全体の構成に注力 |

ツールリップ:「タイムステップシフト。低い値=音質・ディテール重視、高い値=楽曲構造・プロンプト忠実度重視」

### Sampler（サンプリング方式）

| 方式 | 説明 |
|------|------|
| **自動 (ODE)** | 常微分方程式ベース。安定・再現性が高い（デフォルト） |
| ODE | 安定・クリーン |
| SDE | 確率微分方程式ベース。有機的・多様な質感。高ステップ推奨 |

### キャプション自動

| 状態 | 動作 |
|------|------|
| **ON** | ACE-StepのLMによるキャプション強化を使用（推奨） |
| OFF | Easy MusicのLLMが生成したキャプションをそのまま使用 |

### Thinking

| 状態 | 動作 |
|------|------|
| **ON** | LLMがChain-of-Thought推論で簡潔な1文キャプションを生成 |
| OFF | LLMが3〜5文の詳細なキャプションを直接生成 |

---

## 10.6　作詞設定（Normal Mode）

**「✍ 作詞設定」** アコーディオンを展開すると表示されます。

### ムードチップ（10種）

ムードは楽曲の雰囲気を決定します。選択するとキャプション生成時に反映されます。

| チップ | コード値 | 説明 |
|--------|---------|------|
| 😊 明るい | `bright and happy` | ポジティブ、明るい雰囲気 |
| 😢 切ない | `bittersweet and sad` | 切なさ、哀愁 |
| 🔥 激しい | `intense and powerful` | 力強い、エネルギッシュ |
| 🍃 穏やか | `calm and gentle` | 穏やか、リラックス |
| ✨ 神秘的 | `mysterious and fantastical` | 幻想的、ミステリアス |
| 💕 ロマンチック | `romantic and tender` | ロマンティック、優しい |
| 🎉 楽しい | `playful and fun` | 楽しい、陽気 |
| 🌙 メランコリック | `melancholic and dark` | メランコリック、暗い |
| 🏔️ 壮大 | `epic and grand` | 壮大、グランド |
| 😎 クール | `cool and stylish` | クール、スタイリッシュ |

### ボーカルチップ（6種）

ボーカルスタイルを指定します。キャプションに声の特徴が追加されます。

| チップ | コード値 | 説明 |
|--------|---------|------|
| 👩 女声 | `female vocal` | 女性ボーカル |
| 👨 男声 | `male vocal` | 男性ボーカル |
| 🎤 力強い | `powerful vocal` | パワフルなボーカル |
| 🌬️ ウィスパー | `breathy whisper vocal` | ささやくような声 |
| 🎵 ファルセット | `falsetto vocal` | 裏声 |
| 👥 ハーモニー | `vocal harmonies` | コーラス、ハーモニー |

> 💡 ムードとボーカルは同時に選択できます。例えば「✨ 神秘的」+「👩 女声」で「神秘的な雰囲気の女性ボーカル曲」が生成されます。

### テーマ入力

テーマ欄にはAIに作曲の方向性を指示するテキストを入力します。

- **空欄**: LLMがジャンルに合ったテーマを自動生成します
- **入力あり**: 入力されたテーマに基づいて歌詞が生成されます
- **プレースホルダー例**: 「夜空を見上げて願いを込める魔法少女の物語」

### 歌詞入力

歌詞欄にはセクションタグ付きの歌詞テキストを入力します。

- **空欄**: テーマからAIが自動で作詞します
- **入力あり**: 入力された歌詞がそのまま使用されます

対応セクションタグ:
```
[verse]    — Aメロ・Bメロ
[chorus]   — サビ
[bridge]   — ブリッジ、大サビ
[intro]    — イントロ
[outro]    — アウトロ
[pre-chorus] — プレコーラス
[interlude]  — 間奏
```

### 歌詞再生成ボタン（♻️）

歌詞入力欄の横にある **♻️ 再生成** ボタンをクリックすると、現在のテーマとジャンル設定に基づいて歌詞をLLMで再生成します。

### ネガティブプロンプト

生成時に避けたい要素を指定します。

- **空欄時のデフォルト値**: `low quality, noisy, distorted, muddy, clipping, off-key, out of tune, amateur, poorly mixed`
- **カスタム入力**: 避けたい楽器やスタイルを自由に記述

---

## 10.7　おまかせ生成

**「🪄 おまかせ生成」** セクションは、自然言語で1行のリクエストを入力するだけで全パラメータを自動決定する機能です。

### 動作の仕組み

1. 入力テキストをACE-Stepの `/format_input` APIに送信
2. ACE-Step内蔵のLM（Qwen3-Embedding等）がジャンル・BPM・Key・歌詞・キャプションをすべて推定
3. 推定結果に基づいて音楽を生成

> 💡 おまかせ生成ではEasy Music側のLLM（Ollama等）は使用されません。ACE-Stepの内蔵LMが直接処理します。

### 🎲 ランダムボタン

ACE-Stepの `/create_random_sample` APIからランダムなパラメータセットを取得し、UIに自動入力します。取得されるパラメータには、ジャンル、BPM、Key、歌詞、キャプションが含まれます。

言語ドロップダウンで選択中の言語は保持されます。

---

## 10.8　カバーモード

ヘッダーの **「🎤 カバー」** ボタンをクリックするとカバーモードに切り替わります。

### カバーパネルの構成

| 要素 | 説明 |
|------|------|
| **アップロードエリア** | 音声ファイルのドラッグ＆ドロップまたはクリック選択。`accept="audio/*"` |
| **ファイル情報表示** | ファイル名と❌クリアボタン |
| **カバー強度スライダー** | 0.00〜1.00。デフォルト: 0.80 |
| **キャプション入力** | 変換後のスタイル指定（例: jazz, acoustic, lo-fi） |
| **歌詞入力（折りたたみ）** | 任意。新しい歌詞を入力可能 |

### カバー強度の詳細

| 範囲 | 効果 |
|------|------|
| 0.00〜0.20 | 原曲のほぼそのまま。テスト用 |
| 0.20〜0.50 | 軽微な変化。原曲の骨格が明確に残る |
| 0.50〜0.70 | 中程度の変換。メロディの輪郭は残るがアレンジが変化 |
| 0.70〜0.90 | 大幅な変換。ジャンル転換に最適 |
| 0.90〜1.00 | 完全に新しい解釈。原曲との関連が薄い |

> ⚠ カバーモードでは `guidance_scale` が自動的に `1.0` 以上に補正されます。ACE-Step 1.5でカバー生成時に低い `guidance_scale` は品質低下の原因となるためです。

---

## 10.9　リペイントモード

ヘッダーの **「🎨 リペイント」** ボタンをクリックするとリペイントモードに切り替わります。

### リペイントパネルの構成

| 要素 | 説明 |
|------|------|
| **アップロードエリア** | 音声ファイルのドラッグ＆ドロップまたはクリック選択 |
| **再生成区間（秒）** | 開始秒と終了秒を数値入力。step=0.1で0.1秒単位 |
| **キャプション入力** | 再生成部分のスタイル指定（任意） |
| **歌詞入力（折りたたみ）** | 再生成部分の歌詞（任意） |

### 再生成区間の仕様

- **開始秒（Repainting Start）**: 再生成を開始する位置（秒）
- **終了秒（Repainting End）**: 再生成を終了する位置（秒）
- **バリデーション**: 終了秒 > 開始秒 でなければエラー
- 指定区間外の音声はそのまま保持されます

---

## 10.10　JUKEBOXモード

ヘッダーの **「🎶 自動演奏」** ボタンをクリックするとJUKEBOXモードに切り替わります。

### JUKEBOX専用UI

| 要素 | 説明 |
|------|------|
| **ジャンルグリッド（複数選択）** | タイルを複数タップして選択。選択されたジャンルは青くハイライト |
| **選択カテゴリバッジ** | 選択中のジャンルをバッジで表示 |
| **Now Playing表示** | 現在再生中の曲の情報を表示 |
| **▶ スタート / ⏹ ストップ** | 自動生成ループの開始/停止 |
| **シークバー / 音量** | JUKEBOX専用のプレーヤーコントロール |

### 動作フロー

```
1. 選択ジャンルからランダムに1つを選出
2. テーマ自動生成（/api/theme）
3. 歌詞生成（/api/lyrics）
4. キャプション生成（/api/caption）
5. 音楽生成（/api/generate, guidance_scale=18.0）
6. 再生開始
7. 再生中に次の曲をプリフェッチ（バックグラウンドで生成開始）
8. 現在の曲が終了 → プリフェッチ済みの次の曲をシームレスに再生
9. → ステップ1に戻る（無限ループ）
```

### 停止動作

- **⏹ ストップ**: 現在再生中の曲が終わった時点で停止
- 「🛑 現在の曲の再生後に停止します...」というメッセージが表示されます

### 自動リトライ

- 生成失敗時は自動でリトライ（最大3回）
- 3回連続失敗で「❌ 生成に3回失敗しました。JUKEBOXを停止します。」と表示して停止

---

## 10.11　インラインプレーヤーとビジュアライザー

### インラインプレーヤー

楽曲生成完了後に表示されるプレーヤーコントロール。

| 要素 | 説明 |
|------|------|
| **◀ / ▶ トラック切替** | バッチ生成時に複数トラックを切り替え |
| **再生/一時停止ボタン** | 楽曲の再生制御 |
| **シークバー** | クリックまたはドラッグで再生位置を変更 |
| **時間表示** | 現在再生位置 / 総時間 |
| **音量スライダー** | 音量調整 |
| **ダウンロードボタン** | 楽曲をMP3形式でダウンロード |

### フルスクリーンビジュアライザー

プレーヤーエリアをタップするとフルスクリーンのビジュアライザーオーバーレイが表示されます。

#### 5つのビジュアルモード

| モード | 説明 | 技術 |
|--------|------|------|
| **Spectrum** | FFTデータのバー表示。周波数スペクトルを視覚化 | AnalyserNode + getByteFrequencyData |
| **Wave** | 波形データのカーブ表示。リアルタイム波形 | AnalyserNode + getByteTimeDomainData |
| **Ring** | 円環パターンのスペクトル。円状に配置されたバー | 極座標変換 + FFTデータ |
| **Particles** | 音声駆動パーティクルシステム。音に反応する粒子 | パーティクル生成 + 物理シミュレーション |
| **Pulse** | 音量連動パルスエフェクト。ビートに合わせて脈動 | RMS計算 + スケーリング |

#### ビジュアライザーの技術基盤

- **Web Audio API**: `AudioContext` + `AnalyserNode`
- **Canvas 2D**: `requestAnimationFrame` によるリアルタイムレンダリング
- **ジャンル別背景画像**: 各ジャンルに対応した背景が表示される
- **歌詞のリアルタイム表示**: 生成時に使用された歌詞をオーバーレイ表示

画面タップでビジュアルモードが切り替わり、もう一度タップするとオーバーレイを閉じます。

---

## 10.12　生成履歴

**「履歴」** セクション（折りたたみ式）に、直近の生成結果が保持されます。

| 項目 | 説明 |
|------|------|
| **保持件数** | 直近10件 |
| **保存先** | `sessionStorage`（ブラウザタブを閉じるとクリア） |
| **表示内容** | ジャンル名、経過時間、再生ボタン、ダウンロードボタン |
| **経過時間表示** | 〜秒前 / 〜分前 / 〜時間前 / 〜日前 |
| **生成中表示** | 「生成中...」ステータスを表示 |

---

## 10.13　デバッグパネル

**「詳細情報」** ボタンで折りたたみを展開すると、最後の生成で使用されたパラメータの詳細が確認できます。

| 表示項目 | 説明 |
|---------|------|
| **ジャンル** | 選択されたジャンル名 |
| **テーマ** | 使用されたテーマテキスト |
| **モード** | 使用されたモード（キャプション自動/外部LLM/手動等） |
| **タグ (raw)** | LLMが生成したタグ情報（JSON） |
| **キャプション** | 最終的にACE-Stepに送信されたキャプション（**編集可能**） |
| **言語** | 使用された言語コード |
| **パラメータ** | 全パラメータのJSON表示 |

### キャプションの手動編集

デバッグパネルのキャプション欄は `<textarea>` であり、**直接編集が可能**です。編集した内容は次回の生成時に反映されます。

これにより、AIが生成したキャプションを微調整して再生成する、というワークフローが実現できます。

**♻️ 再生成ボタン**: キャプション欄の横にある再生成ボタンで、現在の設定に基づいてキャプションをLLMで再生成できます。

---

## 10.14　モード排他制御

Easy Musicの4つのモード（通常 / カバー / リペイント / JUKEBOX）は**相互排他**です。

| 操作 | 結果 |
|------|------|
| カバーON → リペイントON | カバーが自動OFF |
| リペイントON → JUKEBOX ON | リペイントが自動OFF |
| JUKEBOX実行中 → カバーON | JUKEBOX停止 → カバーON |
| カバーON → カバーOFF | 通常モードに戻る |

通常モードに戻すには、アクティブなモードのボタンをもう一度クリックしてOFFにします。

---

**次章予告**: 第11章では、AIが最高品質の楽曲を生成するためのプロンプトテクニックを解説します。ジャンル別の最適化、おまかせ生成のコツ、キャプション手動編集のノウハウを網羅します。
