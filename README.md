# ScribeJam assets

[ScribeJam](https://github.com/kiwistylegame-hash/ScribeJam) が使う配布ファイルの置き場です。
**ソースコードは入っていません。** アプリ本体・採譜エンジン・学習済みモデルだけです。

アプリは Releases にある `manifest.json` を読み、必要なものだけ取得します。
ファイル名に SHA-256 の頭が入っているので、**中身が変われば URL も変わります**。
古い名前はそのまま残すので、古い版のアプリも壊れません。

## 中身と出典

ここで配っている学習済みモデルは、いずれも第三者が作り、再配布を許しているものです。

| ファイル | 元 | ライセンス |
|---|---|---|
| `nmp-*.onnx` | [Basic Pitch](https://github.com/spotify/basic-pitch)（Spotify） | Apache-2.0 |
| `beat_this-*.onnx` | [Beat This!](https://github.com/CPJKU/beat_this)（CPJKU）を [beat_this_cpp](https://github.com/mosynthkey/beat_this_cpp) が ONNX 化 | MIT（重みも MIT） |
| `time_signature-*.onnx` ほか 4 件 | [PM2S](https://github.com/cheriell/PM2S)（Liu et al.） | コード MIT / **重み CC BY 4.0** |
| `drumsep-*.onnx` | [drumsep](https://github.com/inagoy/drumsep)（inagoy）を [drumsep-onnx](https://huggingface.co/gridshiftstudio/drumsep-onnx) が ONNX 化 | MIT |

ScribeJam 側で加えた変更:

- PM2S … PyTorch のチェックポイントを ONNX へ変換（出力は PyTorch 版と最大誤差 1e-6 で一致）
- drumsep … 重みを fp16 にして 335MB → 167MB（出力差は 16bit WAV の量子化幅以下）

## 帰属表示（CC BY 4.0）

> L. Liu, Q. Kong, V. Morfi and E. Benetos,
> "Performance MIDI-to-Score Conversion by Neural Beat Tracking",
> *Proceedings of the 23rd International Society for Music Information Retrieval Conference (ISMIR)*, 2022.
> モデルの重みは [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) で配布されています。
> ScribeJam はこれを ONNX 形式へ変換して再配布しています。
