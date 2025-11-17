# 日本語支援ツール集 (Japanese-Audio-Tools)

音声・動画ファイルから字幕やAnkiカードを自動生成する日本語支援ツールのコレクションです。Whisper AIによる音声認識とOCR技術を活用し、効率的な語学環境を構築します。

## 📚 収録ツール

### 1. audioGetSrt.ipynb
**音声ファイルからSRT字幕生成**

音声ファイル（MP3など）を日本語音声認識し、タイムライン付きのSRT字幕ファイルを自動生成します。

**特徴:**
- 基本的な音声認識とSRT生成
- 長時間音声（45-60分）のセグメント分割処理
- 単語レベルのタイムスタンプ最適化
- 複数のWhisperモデルサイズ対応（tiny, base, small, medium, large, large-v2）

**使用例:**
- 日本語の音声教材から字幕を作成
- ポッドキャストやオーディオブックの文字起こし

### 2. audioSrtToAnki.ipynb
**動画・音声とSRTからAnkiカード生成**

動画または音声ファイルとSRT字幕ファイルから、Anki用のCSVファイルと分割音声ファイルを自動生成します。

**特徴:**
- 動画から音声を自動抽出
- SRT字幕のタイムスタンプに基づいて音声を分割
- Anki用CSVファイルの自動生成（`[sound:filename.mp3]`形式）
- インポート方法の詳細な説明を含む

**ワークフロー:**
1. 動画ファイルから音声を抽出
2. SRTファイルの各セグメントに対応する音声を切り出し
3. Ankiにインポート可能なCSVファイルを生成

### 3. hardTitlesGetPicOrSrt.ipynb
**ハードコード字幕からAnkiカード生成**

動画に埋め込まれた日英二言語字幕（ハードコード字幕）から、画像とテキストを抽出してAnkiカードを作成します。

**特徴:**
- 画像の上下分割（日本語60% / 英語40%）
- OCRによるテキスト抽出
- SRTファイルのクリーンアップ機能
- VideoSubFinder、AABBYと連携

**対象:**
- 日英二言語字幕が埋め込まれた動画
- ハードコード字幕付きアニメやドラマ

### 4. mp3ToLrc.ipynb
**音声からLRC歌詞ファイル生成**

日本語音声ファイルからLRC形式の歌詞ファイルを生成します。Google Colab環境での実行を想定。

**特徴:**
- LRC形式（`[mm:ss.xx]`）のタイムスタンプ生成
- バッチ処理対応（複数ファイルの一括処理）
- ZIP圧縮によるダウンロード機能
- Google Colab GPU利用で高速処理

**使用例:**
- 日本語楽曲の歌詞作成
- 音声教材のLRCファイル生成

## 🛠️ 必要な環境

### Python パッケージ
```bash
pip install openai-whisper
pip install torch torchvision torchaudio
pip install numpy
pip install pydub
pip install moviepy
pip install pysrt
pip install pillow
```

### 外部ツール
- **ffmpeg**: 音声・動画処理に必須
  - Windows: https://www.gyan.dev/ffmpeg/builds/
- **VideoSubFinder**: ハードコード字幕の抽出（hardTitlesGetPicOrSrt.ipynb用）
- **AABBY OCR**: 画像からテキスト抽出（hardTitlesGetPicOrSrt.ipynb用）

### ハードウェア推奨
- **GPU**: CUDA対応のNVIDIA GPU（Whisperの高速処理に推奨）
- **CPU**: GPUなしでも動作しますが、処理時間が大幅に増加します

## 🚀 使い方

### 基本的な流れ

1. **音声認識でSRT生成** (`audioGetSrt.ipynb`)
   ```python
   AUDIO_PATH = "/path/to/your/audio.mp3"
   # セルを実行してSRTファイルを生成
   ```

2. **AnkiカードのCSV生成** (`audioSrtToAnki.ipynb`)
   ```python
   VIDEO_PATH = "/path/to/your/video.mp4"
   SRT_PATH = "/path/to/your/subtitle.srt"
   # セルを順次実行してCSVと音声ファイルを生成
   ```

3. **Ankiにインポート**
   - 生成された音声ファイルをAnkiのmediaフォルダにコピー
   - CSVファイルをAnkiにインポート

### ファイルパスの設定

各ノートブックの先頭で、以下のような変数を自分の環境に合わせて変更してください：

```python
AUDIO_PATH = "/path/to/your/audio.mp3"
VIDEO_PATH = "/path/to/your/video.mp4"
SRT_PATH = "/path/to/your/subtitle.srt"
```

## 📝 ライセンス

このプロジェクトはMITライセンスの下で公開されています。

## 🤝 貢献

バグ報告、機能提案、プルリクエストを歓迎します！

## ⚠️ 注意事項

- 音声認識の精度は音声品質や話速度に依存します
- 大量のファイルを処理する場合、ディスク容量に注意してください
- 著作権で保護されたコンテンツを扱う際は、適切な権利処理を行ってください

## 📧 お問い合わせ

質問や提案がある場合は、GitHubのIssuesでお知らせください。

---

**Happy Learning! 🎌📚**
