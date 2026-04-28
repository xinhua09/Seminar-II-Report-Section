2026/04/28 書報討論重點整理
===
11463110 張心䛡  
講者：國立雲林科技大學資訊工程系許正欣副教授
講題：A Lightweight-Embedded Open-Set Speaker Identification System Based on Meta Learning
---

## 重點整理

1. 講者背景
    * 博士班研究領域：通訊（論文為 3G 行動通訊）
    * 博士後：4G
    *  升等後：5G
    * 目前也關注 6G，但近年轉向語音相關研究（語者辨識已做約 7-8 年）
    * 研究成果：多項美國與臺灣專利、執行多項計畫，技術已相當成熟

2. 語者辨識（Speaker Recognition）定義
    * 透過說話者的語音來辨識說話者的身份
    * 主要目的：
        * 阻擋 冒充者（Imposter）：非註冊語者試圖闖入系統
        * 阻擋 欺騙攻擊（Spoofing Attacks）：使用錄音、合成、轉換等假造語音攻擊系統

3. 欺騙攻擊（Spoofing Attacks）類型
    * 人聲模仿（Impersonation）：如同卵雙胞胎聲音相似
    * 錄音回放（Replay Attack）：最常見、成本最低
    * 語音合成（Speech Synthesis / TTS）：如雲端語音合成（現已非常成熟）
    * 語音轉換（Voice Conversion）：將一人聲音轉換成另一人聲音
    * 物理性訪問（Physical Access）：透過麥克風播放假聲音（會經過麥克風通道效應）
    * 邏輯性訪問（Logical Access）：繞過麥克風，直接將音檔輸入系統（無麥克風效應）

4. 語者辨識系統的兩大任務
    * 語者驗證（Speaker Verification）：
        * 二元分類（是/不是本人）
        * 典型應用：手機語音解鎖（如 Siri + 聲紋）

    * 語者識別（Speaker Identification）：
        * 多元分類（從多個註冊語者中辨識是誰）
        * 典型應用：實驗室門禁、會議記錄等

5. 本文相關 vs 本文無關

    * 本文相關（Text-Dependent）：
        * 需說固定密語（如「芝麻開門」）
        * 安全性較高，但訓練困難（需大量多樣化資料）

    * 本文無關（Text-Independent）：
        * 說任何內容皆可辨識
        * 更實用，目前主流採用此方式


6. 早期系統架構（傳統機器學習時期）

    * 兩個階段：
        1.  欺騙攻擊偵測階段（Spoofing Detection）
            * 使用 CQCC（Constant Q Cepstral Coefficients）特徵
            * 二元分類：真人語音 vs 假造語音（錄音/合成）

        2. 語者辨識階段
            * 使用 MFCC + i-vector 等特徵
            * 整體學習（Ensemble Learning）：多個模型組合（Single-Model DNN、Multi-Model DNN、Linear SVM、Kernel SVM、Random Forest 等）

    * 決策方式：門檻值（Threshold） + 分數正規化

7. 重要語音特徵提取

    * CQCC（Constant Q Cepstral Coefficients）：
        * 結合 CQT（Constant Q Transform）
        * 對頻率變化更敏銳，符合人耳聽覺系統
        * 特別適合偵測欺騙攻擊（維度約 60 維）

    * i-vector：
        * 基於 Joint Factor Analysis（JFA）
        * 將變動長度的語音特徵轉為固定長度（通常 400 維）
        * 使用 UBM（Universal Background Model）建立背景模型


8. 整體學習（Ensemble Learning）

    * 當單一模型不夠強（資料少、計算資源有限）時，使用多個弱分類器組合
    * 優點：互補強弱，提升整體效能
    * 決策方式：
        * 多數決（Majority Voting）
        * 全數決（Unanimity Voting）：所有模型都同意才放行（更嚴格防冒充者）


9. 系統挑戰與解決方案

    * 資料問題：真實世界語料稀疏、環境差異大（實驗室表現好，真實環境差）
    * 長短語音問題：註冊時語音較長，使用時語音較短 → 後期用深度學習 + meta-learning 解決
    * 錯誤拒絕（False Rejection）：註冊語者被錯誤拒絕 → 採用 Conditional Retry（條件性重試） 機制
    * 門檻值取捨（Trade-off）：
        * 提高阻擋率（防冒充者）→ 可能降低通過率（影響合法使用者）
        * 反之亦然


10. 後續發展與現況

    * 早期使用傳統機器學習 + 整體學習
    * 後期轉向輕量級深度學習模型（small model），適合嵌入式系統（如 NVIDIA Jetson TX2）
    * 目前已不再主力做語者辨識，轉向：
        * 語音情緒辨識
        * 臺語語音辨識 / 語音合成
        * 低資源語言處理

    * 在學校做研究的現實：熱門領域被大廠壟斷，需找利基（niche）如低資源語言、跨領域應用

11. 投影片重點補充

    * 系統需同時處理 冒充者、目標語者、欺騙攻擊 三類輸入
    * 欺騙攻擊偵測模型可使用 RNN 解決輸入長度不一問題
    * 整體學習可進一步超參數最佳化，降低複雜度並提升效能
    * 實作平台：NVIDIA Jetson TX2 + 麥克風，可實際部署於嵌入式裝置

