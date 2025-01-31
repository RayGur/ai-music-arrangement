# Music Arrangement Tool

將流行樂自動轉換為管樂團編曲的工具。本專案是一個自動化系統，能夠分析流行音樂的特徵，並根據管樂器的特性生成合適的管樂團編曲。


## 系統需求


## 安裝說明

```bash
git clone https://github.com/yourusername/music-arrangement-tool.git
cd music-arrangement-tool
pip install -r requirements.txt
```

## 開發指南

### 分支管理

我們採用 Git Flow 工作流：

- `main`: 穩定的生產版本
  - 只接受來自 `develop` 和 `hotfix/*` 的合併
  - 每個合併都會產生新的版本標籤
  
- `develop`: 開發版本
  - 包含最新的開發特性
  - 作為特性分支的基礎
  
- `feature/*`: 新功能開發
  - 從 `develop` 分支出
  - 完成後合併回 `develop`
  
- `bugfix/*`: 錯誤修復
  - 用於修復 `develop` 分支中的問題
  
- `hotfix/*`: 緊急修復
  - 用於修復生產版本中的問題
  - 從 `main` 分支出
  - 同時合併回 `main` 和 `develop`

### 提交規範

我們使用 [Conventional Commits](https://www.conventionalcommits.org/) 規範：

- `feat`: 新功能
  - 例：`feat: 添加長笛音域檢查功能`

- `fix`: 錯誤修復
  - 例：`fix: 修正換氣點計算錯誤`

- `docs`: 文件更新
  - 例：`docs: 更新安裝說明`

- `style`: 程式碼格式調整
  - 例：`style: 統一縮排格式`

- `refactor`: 程式碼重構
  - 例：`refactor: 重構樂器分配邏輯`

- `test`: 測試相關
  - 例：`test: 添加特徵提取測試`

- `chore`: 維護工作
  - 例：`chore: 更新依賴版本`

### 開發流程

1. 建立新分支
```bash
git checkout develop
git pull
git checkout -b feature/your-feature-name
```

2. 開發並提交
```bash
git add .
git commit -m "feat: add your feature"
```

3. 推送分支
```bash
git push origin feature/your-feature-name
```

4. 創建 Pull Request
- 在 GitHub 上創建 PR
- 選擇目標分支（通常是 `develop`）
- 等待程式碼審查

