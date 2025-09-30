# MIPS-like 5-Stage Pipelined CPU with Hazard Handling

![Language](https://img.shields.io/badge/Language-Verilog-blue.svg)
![Simulator](https://img.shields.io/badge/Simulator-Icarus%20Verilog-green.svg)

這是一個使用 Verilog 設計並實作的 MIPS-like 高效能處理器。專案最終成果為一顆功能完整的 5-Stage Pipeline CPU，並具備了處理 Data Hazard 的功能。

## Key Features

-   **5-Stage Pipeline **
    -   將指令執行流程切分為五個階段：IF (指令擷取), ID (指令解碼), EX (執行), MEM (記憶體存取), WB (寫回)。
    -   在階段之間插入管線暫存器 (Pipeline Registers)，大幅提升處理器的 Throughput。

-   **Data Forwarding **
    -   設計了Forwarding Unit 來偵測並解決Data Hazards。
    -   將最新運算結果從後續管線階段直接傳遞至 EX 階段的 ALU 輸入端，有效減少不必要的管線停頓 (Stall)。

-   **Stall for Load-Use Hazard **
    -   設計了 Hazard Detection Unit 來專門處理 `load-use` 型別的 Data Hazard。
    -   當偵測到 `load-use` 情況時，管線會暫停 (Stall) 一個週期，以確保資料能從記憶體被正確讀取後再進行使用。

## Architecture

處理器的整體架構圖如下所示，包含了五個管線階段以及 Hazard Handling 的相關單元。

<p align="center">
  <img width="878" height="541" alt="image" src="https://github.com/user-attachments/assets/4afa5b6b-87bd-415d-962c-feb0933eb76e" />

</p>


## Environment

-   **HDL**: Verilog
-   **Simulator**: Icarus Verilog (`iverilog`)
-   **Waveform Viewer**: GTKWave 

