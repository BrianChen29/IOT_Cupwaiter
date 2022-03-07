# Cupwaiter proposal

### 簡介
機械式手臂杯架，根據使用者動作，跟隨使用者的杯架。根據使用者手勢動作及與使用者的距離，跟隨使用者的杯架，提供使用者放置杯架及其延伸功能，像是一位專業的服務人員的感覺。

### 專題發想
有時在辦公或是讀書時桌上很混亂這時一個杯子在那更是占空間，況且還有打翻飲料導致紙本資料及破壞電腦的風險，這時需要個自動移動式杯架，在我們需要喝東西的時候遞到我們的手上，在我們需要維持桌面整潔時騰出空間。

### 詳細描述
利用使用者前方的鏡頭得到影像，分析使用者的動作，辨識到手拿著杯子往前伸的動作時，杯架自動往前伸至使用者面前；偵測到背架上的重量後收回機械手臂。手再次往前伸或是根據語音辨識到使用者說出「我要喝xxx」的字眼，機械手臂會再次往前伸至使用者面前，讓使用者拿取杯子。若要泡粉狀飲品(茶粉、咖啡、蛋白粉)可以幫忙搖勻或是攪拌均勻(利用手機line bot選擇: 搖:機械手臂上下快速擺動 攪拌:利用磁力攪拌棒(馬達+磁鐵))
##### (-new)想要享受那種飯來張口茶來伸手的感覺 倒水的功能
#### 可擴充功能:
* 根據溫度計測溫度回傳手機再利用溫控器保溫或保冷
* 根據重量自動加水
* 製作手搖飲

### 物品描述
* 使用者前方有一鏡頭偵測使用者的動作
* 杯架根據使用者位置及手勢移動至適當的位置
* 杯架是連接著機械手臂幫助杯架移動
* 利用磁吸攪拌棒以及杯座的磁鐵+馬達以達到攪拌效果

### 示意圖


### 硬體材料、工具

| 品項               | 數量 | 用途                            | 購買連結                 |
|:------------------ | ---- | ------------------------------- | ------------------------ |
| Raspberry pi       | 1    |                                 |                          |
| 機械手臂           | 1    | 連結杯架、掌控杯架的移動        | https://reurl.cc/r8eErZ  |
| 杯架               | 1    | 放容器的地方                    | https://reurl.cc/Z7molQ    |
| 鏡頭               | 1    | 捕捉使用者影像                  | 原有                     |
| 超聲波傳感器       | 1    | 測量杯架與使用者距離            | 原有                     |
| 紅外線傳感器       | 1    | 測量杯架與使用者距離            | 原有                     |
| 16路舵機PWM控制板  | 1    | 驅動機械手臂                    | https://reurl.cc/7oa9jN/ |
| 馬達               | 1    | 攪拌                            | 原有                     |
| L298N             | 1    | 驅動馬達                        | 原有                     |
| 磁鐵               | 1    | 攪拌(接在馬達上 吸住磁力攪拌棒) | https://reurl.cc/r8e2W4  |
| 磁力攪拌棒         | 1    | 攪拌                            | https://reurl.cc/av30G7  |
| HX711+壓力感測器組 | 1    | 秤重                            | https://reurl.cc/Gr1nKv  |
| 抽水幫浦           | 1    | 自動加水功能                    | https://reurl.cc/bRQ4dv  |

### 參考資料
* 手勢偵測概念實做+範例程式碼
https://medium.com/@CLiu13/gesture-detection-with-a-raspberry-pi-f72a6038e967

* openvino model zoo 各種動作偵測
https://github.com/openvinotoolkit/open_model_zoo


* 利用Raspberry Pi, NCS2 做姿勢估測 pose estimation
https://community.intel.com/t5/Intel-Distribution-of-OpenVINO/Human-pose-estimation-model-on-Raspberry-pi-4-with-NCS2/td-p/1206347

* 利用 Raspberry Pi, Python, OpenCV, and Dropbox做空間監測及動作偵測+範例程式碼
https://www.pyimagesearch.com/2015/06/01/home-surveillance-and-motion-detection-with-the-raspberry-pi-python-and-opencv/

* 手機操控機械手臂+車車
https://www.youtube.com/watch?v=LBNRGBY5zN8&ab_channel=HowToMechatronics

* raspberry pi 利用搖桿操控機械手臂
https://www.youtube.com/watch?v=1aT8bETAUGk&ab_channel=%E8%89%BE%E9%8D%97

* 跟著人移動的機器人(目標檢測+跟蹤問題) 
https://www.mdeditor.tw/pl/2on5/zh-tw

* 利用Line Bot 操控家電
https://sites.google.com/jes.mlc.edu.tw/ljj/linebot%E5%AF%A6%E5%81%9A/%E5%A6%82%E4%BD%95%E7%94%A8linebot%E6%8E%A7%E5%88%B6%E5%AE%B6%E9%9B%BB

* Mirobot(mini-industrial robot arm) 做各種事的機械手臂 
https://www.youtube.com/watch?v=SisrRUX_Zfk&ab_channel=CFOG
https://www.kickstarter.com/projects/mirobot/mirobot-6-axis-mini-industrial-robot-arm?ref=9454f8&utm_source=og-social

* tensorflow 姿勢估測
https://www.tensorflow.org/lite/models/pose_estimation/overview?hl=zh_tw

* 機械手臂 組裝
https://www.taiwansensor.com.tw/6%E8%BB%B8%E6%A9%9F%E6%A2%B0%E6%89%8B%E8%87%82%E7%B5%84%E8%A3%9D%E6%95%99%E5%AD%B8/

* 利用python做手勢識別與控制(with openCV)
https://kknews.cc/zh-tw/code/a68ega6.html
