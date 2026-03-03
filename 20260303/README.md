2026/03/03 書報討論重點整理
===
11463110 張心䛡  
講者：國立中正大學光機電整合工程研究所 葉志庭副教授  
講題：Mini/Micro LED Design and Challenges for Advanced Displays
---

## 重點整理

* Mini LED 與 Micro LED 的基本定義、尺寸區分與製造流程
* 兩者差異（常以晶片尺寸 <100μm 且無藍寶石基板作為 Micro LED 分界，或依觀看距離決定）
* 應用領域：電視、車用顯示、AR/VR、穿戴裝置、遊戲螢幕等
* Mini LED 背光技術進展（包括局部調光、高亮度、薄型化設計）
* Micro LED 顯示器設計重點：提升 EQE（外部量子效率）、視角、色純度
* RGB Micro LED vs. 彩色轉換（Color Conversion，如藍光+量子點）比較
* 大尺寸 Micro LED 量產挑戰（Mass Transfer、死點修復、良率、COC/COW 製程）
* 人眼解析度極限與不同裝置所需 PPI（AR/VR 需極高 PPI）
* LCD / OLED / Mini LED / Micro LED 性能雷達圖比較
* Micro LED 先進設計三大方向：
    * 磊晶結構優化：調整多量子井、p-GaN / n-GaN 厚度、InGaN 井層比例等參數，提升發光效率與波長一致性。例如投影片展示典型結構：150 nm p-GaN、5 對 MQWs、u-GaN / n-GaN 緩衝層等，晶片尺寸可達 1.5 µm，並附 SEM 截面圖驗證側壁鈍化品質。
    * 發射角度調整：目標達成全角度發光，避免傳統 Micro LED 光束過窄導致視角差。使用高度反射薄膜優化：結合低吸收介電質薄膜和高反射金屬膜，反射側壁光線，擴大出光角度至接近全向）。
    * 全彩解決方案：討論 RGB 三色獨立晶片 vs. 藍光 + 彩色轉換（QD 或 phosphor）的優缺點，強調色純度提升、良率與修復挑戰。
* 製造流程重點：
    * Chip on Wafer (CoW)：展示側視與頂視結構，p-GaN 上使用 ITO 透明電極 + Ti/Au 或 Au/Sn 焊墊，n-GaN 共用或獨立 N 墊設計，目的是減少 N 電極數量、提升bonding良率。
    * 標準 Micro LED 晶片製程：從 EPI 磊晶 → Mesa 蝕刻 → ICP RIE 隔離 → 鈍化（passivation） → Pad 製作 → ITO 蝕刻等步驟，強調側壁處理避免漏電與表面缺陷。
* Micro LED 與 Mini LED 在資工領域的關聯性包含影像演算法與即時計算系統。
* 要實現高對比、局部調光、高幀率、無閃爍，需要複雜的演算法：
    * 色彩校正與均勻性補償
    * 動態範圍映射
    * 視角補償
    * 針對 AR/VR 的低延遲渲染、foveated rendering
