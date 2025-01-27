# 專案結構說明

## 目錄結構
```
music-arrangement-tool/
├── .gitignore               # Git 忽略檔案配置
├── README.md               # 專案主要說明文件
├── requirements.txt        # Python 套件依賴
├── setup.py               # 專案安裝配置
│
├── config/                # 配置檔案目錄
│   ├── instruments.json        # 樂器配置
│   └── arrangement_rules.json  # 編曲規則
│
├── src/                   # 源代碼目錄
│   ├── __init__.py
│   ├── audio_processing/       # 音訊處理相關
│   │   ├── __init__.py
│   │   ├── stem_separator.py   # Demucs 處理
│   │   └── feature_extractor.py # 特徵提取
│   │
│   ├── arrangement/           # 編曲邏輯相關
│   │   ├── __init__.py
│   │   ├── rules_engine.py    # 規則引擎
│   │   ├── instrument_assign.py # 樂器分配
│   │   └── optimizer.py       # 優化處理
│   │
│   ├── data/                  # 資料處理相關
│   │   ├── __init__.py
│   │   ├── music_features.py  # 音樂特徵定義
│   │   └── instrument_db.py   # 樂器資料庫
│   │
│   └── output/               # 輸出處理相關
│       ├── __init__.py
│       ├── midi_generator.py  # MIDI生成
│       └── score_generator.py # 樂譜生成
│
├── tests/                    # 測試檔案
│   ├── __init__.py
│   ├── test_audio_processing/
│   ├── test_arrangement/
│   └── test_output/
│
├── examples/                 # 範例檔案
│   ├── input_examples/      # 輸入音訊範例
│   └── output_examples/     # 輸出結果範例
│
└── docs/                    # 文件
    ├── api/                 # API文件
    ├── usage/              # 使用說明
    └── development/        # 開發指南
```

## 核心模組說明

### 1. audio_processing (音訊處理)
處理原始音訊檔案和進行特徵提取的模組。

#### stem_separator.py
- 使用 Demucs 進行音源分離
- 將原始音訊分離為人聲、主旋律、和聲等不同聲部

#### feature_extractor.py
- 使用 librosa 和 mir_eval 進行特徵提取
- 分析音高、節奏、和聲等音樂特徵

### 2. arrangement (編曲處理)
負責將音樂特徵轉換為管樂編曲的核心模組。

#### rules_engine.py
- 實現編曲規則的處理引擎
- 定義和執行編曲規則

#### instrument_assign.py
- 實現樂器分配邏輯
- 使用決策樹和評分系統進行分配

#### optimizer.py
- 優化編曲結果
- 處理樂器間的平衡和衝突

### 3. data (資料處理)
管理音樂特徵和樂器資料的模組。

#### music_features.py
- 定義音樂特徵的資料結構
- 處理特徵資料的轉換和存儲

#### instrument_db.py
- 管理樂器資料庫
- 提供樂器特性的查詢接口

### 4. output (輸出處理)
負責生成最終輸出文件的模組。

#### midi_generator.py
- 生成 MIDI 檔案
- 處理 MIDI 相關的轉換

#### score_generator.py
- 生成樂譜檔案
- 處理 MusicXML 和 PDF 輸出

## 資料流程

```
原始音訊 -> 音源分離 -> 特徵提取 -> 樂器分配 -> 優化處理 -> 最終輸出
```

1. 音源分離階段
   - 輸入：原始音訊檔案
   - 輸出：分離後的 STEM 檔案

2. 特徵提取階段
   - 輸入：STEM 檔案
   - 輸出：音樂特徵資料（JSON格式）

3. 樂器分配階段
   - 輸入：音樂特徵資料
   - 輸出：初步的樂器分配方案

4. 優化處理階段
   - 輸入：初步分配方案
   - 輸出：優化後的編曲結果

5. 輸出生成階段
   - 輸入：最終編曲結果
   - 輸出：MIDI/MusicXML/PDF 檔案

## 配置文件

### instruments.json
定義各種管樂器的特性和限制：
- 音域範圍
- 演奏技巧
- 音色特徵
- 呼吸限制

### arrangement_rules.json
定義編曲規則和模式：
- 旋律分配模式
- 和聲處理規則
- 樂器組合模式
