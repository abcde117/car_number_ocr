# Car License Plate Recognition using YOLOv8 and EasyOCR  
YOLOv8とEasyOCRを用いた車のナンバープレート認識

## 📌 Project Overview | プロジェクト概要

This project aims to detect and recognize car license plates using a combination of **YOLOv8 (for object detection)** and **EasyOCR (for optical character recognition)**.  
本プロジェクトでは、**YOLOv8（物体検出）**と**EasyOCR（光学文字認識）**を組み合わせて、車のナンバープレートを検出・認識することを目的としています。

---

## 📁 Dataset | データセット

We use the open dataset [car-plate-detection](https://www.kaggle.com/datasets/andrewmvd/car-plate-detection) from Kaggle.  
Kaggle上のオープンデータセット [car-plate-detection](https://www.kaggle.com/datasets/andrewmvd/car-plate-detection) を使用しています。

- Contains annotated images and bounding boxes of car license plates.  
- 車のナンバープレートにアノテーションされた画像とバウンディングボックスが含まれています。

---

## 🔧 Main Steps | 主な処理ステップ

1. **Data Preparation | データ準備**  
   XML annotations are converted to YOLO format, and data is split into train/val/test.  
   XML形式のアノテーションをYOLO形式に変換し、train/val/testに分割します。

2. **Training YOLOv8 | YOLOv8モデルの学習**  
   A YOLOv8 model is trained on the dataset to detect license plates.  
   ナンバープレート検出のためにYOLOv8モデルを学習させます。

3. **Detection + OCR | 検出と文字認識**  
   Detected plate areas are cropped and passed to EasyOCR for text extraction.  
   検出された領域を切り出し、EasyOCRで文字を認識します。

4. **Encapsulation | クラス化**  
   A class wraps the pipeline into two functions: `extraction()` and `recognize()`.  
   一連の処理を`extraction()`と`recognize()`の2つの関数にまとめたクラスを実装しています。

---

## 🖼️ Example | 実行例

```python
result = Result(model, reader)
images = result.extraction("/content/1.jpg")
text = result.recognize()
print(text)
