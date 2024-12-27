# PdfToTextAndImage

このリポジトリは、PDFからテキストと画像を抽出するPythonスクリプトを提供します。

## 必要な環境

- Python 3.6以上
- ライブラリ: pdf2image, pyocr, Pillow
- ツール: Tesseract-OCR, Poppler

## インストール

1. ライブラリをインストール:

   ```bash
   pip install pdf2image pyocr Pillow
   ```

2. Tesseract-OCR と Poppler をインストール:
   - macOS: Homebrewで `brew install tesseract poppler`
   - Windows: 各公式サイトからインストール

## 使い方

1. **Tesseractのパス設定**:

   ```python
   import pyocr
   pyocr.tesseract.TESSERACT_CMD = r'パスを指定'  # Windowsの場合
   ```

2. **PDFを画像に変換**:

   ```python
   from pdf2image import convert_from_path
   images = convert_from_path('sample.pdf', dpi=300)
   ```

3. **画像からテキスト抽出**:

   ```python
   tool = pyocr.get_available_tools()[0]
   text = tool.image_to_string(images[0], lang='jpn')
   ```

4. **結果を保存**:

   ```python
   with open('output.txt', 'w', encoding='utf-8') as f:
       f.write(text)
   ```

## 注意事項

- 日本語OCRを利用する場合、Tesseractの日本語データをインストールしてください。
- PDFの内容によっては、抽出精度が異なります。

## 詳細

詳細なコードは`figure.ipynb`をご参照ください。

