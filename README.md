# Google-meet Parasite 互動式透明白板

## 使用步驟

1. 安裝依賴套件

```bash
npm install
```

2. 更新 descriptor
   使用 chrome 打開 Google meet，將 Google meet 的會議 ID 分別覆寫至以下檔案（./descriptor/ChromeGoogleMeet/）:

```bash
Google-meet-roomID.json
```

3. Google meet 點選"顯示所有參與者"
   ![1719983412569](image/README/1719983412569.png)
   ![1719983543166](image/README/1719983543166.png)

4. 啟動 Parasite
    * 期間請讓Google meet保持在畫面最頂部
```bash
npm start
```

5. 點選 Google meet 頁面，讓他 focus，Google meet 的部分會有綠色框線，並且左側會出現三個按鈕(連線、白板、彈幕)。
   ![1719984105272](image/README/1719984105272.png)

6. 按下連線按鈕，會跟 server 建立 web socket 通道進行溝通。
   出現已連線代表連線成功，可以開始使用白板及彈幕功能。
   ![1719984344333](image/README/1719984344333.png)

7. 安裝影片
    [![Google-meet Parasite 互動式透明白板 - 安裝demo](https://img.youtube.com/vi/ps_U1vNYl3A/maxresdefault.jpg)](https://youtu.be/ps_U1vNYl3A)

## UI介紹
* 整體畫面
    ![整體UI](image/README/整體UI.png)

* 功能按鈕
    ![工具列](image/README/工具列.png)

    * 連線按鈕
        * ![連線](image/README/連線.png)
        * 點擊後可與伺服器建立連線，並藉由伺服器與他人連線

    * 白板按鈕
        * ![白板](image/README/白板.png)
        * 點擊後開啟白板，在白板範圍內（綠色的粗框框）可以利用白板工具欄內的工具進行編輯
        

        * 白板生效範圍：
            * 若當前**無人**分享畫面
            白板不會出現
            ![無白板模式](image/README/無白板模式.png)

    
            * 若當前**你**在分享畫面
                * 可選擇分享視窗或者分享整個螢幕
                * 並在**白板工具欄**中**選擇對應的分享模式**：
                    * 分享螢幕：![分享螢幕](image/README/分享螢幕.png)
                        * 白板生效範圍為全螢幕
                    * 分享視窗：![分享視窗](image/README/分享視窗.png)
                        * 白板生效範圍為全螢幕減去Windows工作列的範圍
                        * **注意：若要分享視窗，請將該視窗最大化，以進行白板間的互動**
            
            ![講者模式](image/README/講者模式.png)

    
            * 若當前**其他人**在分享畫面
            白板生效範圍為被分享的畫面顯示的範圍
            ![聽眾模式](image/README/聽眾模式.png)

    * 彈幕按鈕
        * ![彈幕](image/README/彈幕.png)
            * 點擊後展開彈幕的功能按鈕：![彈幕功能](image/README/彈幕功能.png)
            
            * 發送彈幕（需先點擊連線按鈕連線才可使用）

                * 彈幕發送點擊按鈕： ![彈幕](image/README/彈幕.png)
                * 點擊後展開信息輸入框： ![彈幕_輸入框](image/README/彈幕_輸入框.png)
                * 可在輸入框中輸入內容，點擊發送按鈕送出：![彈幕發送](image/README/彈幕發送.png)
                * 可以選擇勾選匿名選項： ![匿名彈幕](image/README/匿名彈幕.png)
                * 發送的信息前面不會屬名： ![匿名的彈幕](image/README/匿名的彈幕.png)
    
            * 選擇接收彈幕的人員
                * 點擊： ![選擇人員](image/README/選擇人員.png)
                * 會顯示當前連線到伺服器（點擊了連線按鈕）的人員: ![人員列表](image/README/人員列表.png)
                * 在發送彈幕時，會向被彈幕勾選的人員發送彈幕
                * 若是**沒有勾選任何人員**，則向**所有人**發送彈幕（指有連線的所有人）
    
    * 傳輸按鈕
        * ![傳輸](image/README/傳輸.png)
        * 需先連線才能上傳/下載檔案
            * 點擊後展開傳輸的功能列表：![檔案傳輸](image/README/檔案傳輸.png)
                * 被上傳的檔案：![上傳的檔案](image/README/上傳的檔案.png)
                    * 刪除檔案（只會刪除本地檔案）：![刪除檔案](image/README/刪除檔案.png)
                    * 下載檔案：![下載檔案](image/README/下載檔案.png)
                * 上傳檔案：![上傳](image/README/上傳.png)
                * 關閉列表：![關閉](image/README/關閉.png)
                

* 白板工具欄：
    * 樣式為：![白板工具欄_收起](image/README/白板工具欄_收起.png)
    * 可以被滑鼠拖動，放在覺得適當的位置
    * 點擊後展開：![白板工具欄_展開](image/README/白板工具欄_展開.png)

    * 工具欄中的工具（只能用於白板範圍）：
        * 畫筆：![畫筆](image/README/畫筆.png)
            * 可跟隨滑鼠軌跡留下軌跡

        * 文字輸入：![文字輸入](image/README/文字輸入.png)
            * 可以在白板中指定位置輸入文字

        * 圖案：![圖案](image/README/圖案.png)
            * 點擊後展開：![圖案_選擇](image/README/圖案_選擇.png)
            * 可選
                * 橢圓
                * 矩形
                * 直線
        * 橡皮擦：![橡皮擦](image/README/橡皮擦.png)
            * 滑鼠左鍵按下並移動可以擦除鼠標位置上的白板內容

        * 顏色：![顏色](image/README/顏色.png)
            * 可以選擇畫筆、文字輸入、圖案功能的顏色
            * 點擊後展開：![顏色選擇](image/README/顏色選擇.png)
            * 可選更多顏色：![更多顏色](image/README/更多顏色.png)
                * 點擊後開啟更多顏色的選擇介面：![顏色選擇器](image/README/顏色選擇器.png)
                * 若選擇到當前顏色選擇欄位中不存在的顏色，會將第二列中的顏色往右移（刪除該列最右側的顏色），後將選擇的顏色插入第二列最左邊
                * 例如選取顏色：![其他顏色選擇](image/README/其他顏色選擇.png)
                * 列表會更新為：![顏色選擇_記錄顏色](image/README/顏色選擇_記錄顏色.png)
            

        * 粗細：![粗細](image/README/粗細.png)
            * 點擊後展開：![粗細選擇](image/README/粗細選擇.png)
            * 可以選擇畫筆、文字輸入、圖案、橡皮擦功能的粗細

        * 虛線：![虛線](image/README/虛線.png)
            * 點擊後展開：![樣式選擇](image/README/樣式選擇.png)
            * 可以讓畫筆、圖案、橡皮擦功能變為虛線的形式
        
        * 清除：![清除](image/README/清除.png)
            * 清除白板上的所有內容
        
        * 可見/隱藏他人對於你的白板的編輯：![可見他人的編輯Parasite](image/README/可見他人的編輯.png)
            * 點擊後切換：![隱藏他人的編輯](image/README/隱藏他人的編輯.png)
            * 若當前為：![可見他人的編輯Parasite](image/README/可見他人的編輯.png)
                * 可以看見他人對於你的白板的編輯紀錄
            * 若當前為：![隱藏他人的編輯](image/README/隱藏他人的編輯.png)
                * 他人對於妳的白板的編輯會被隱藏

        * 當前編輯白板：
            * 若當前為聽眾或者無白板狀態，可點擊切換：
                * 我的白板：![我的白板](image/README/我的白板.png)
                    * 編輯自己的白板
                * 講者白板：![講者白板](image/README/講者白板.png)
                    * 編輯講者白板，該模式下對白版的編輯會同步到講者的白板
                    * 需要**連線**，才能進行白板編輯的同步

            * 若當前為講者狀態，可點擊切換：
                * **請依分享方式手動切換對應模式**
                * **請先行連線才能進行白板編輯的同步**
                * 分享螢幕：![分享螢幕](image/README/分享螢幕.png)
                    * 進行分享時選擇分享整個螢幕請選擇此模式

                * 分享視窗：![分享視窗](image/README/分享視窗.png)
                    * 進行分享時選擇分享個別視窗請選擇此模式
                    * 請將分享的視窗**最大化**
    

        * 截圖：![截圖](image/README/截圖.png)
            * 截圖當前分享的螢幕畫面
            * 紀錄當前白板內容

        * 查看截圖：![儲存](image/README/儲存.png)
            * 開啟儲存（翻頁）面板
    
    * 儲存（翻頁）面板：![儲存（翻頁）面板](image/README/儲存（翻頁）面板.png)
        * 觀看被擷取過的圖片（會同步顯示擷取圖片時的白板內容），方向鍵切換頁面
        * 編輯被擷取過的圖片，功能同白板工具欄內的工具（使用白板工具欄選擇工具）
        * 裁切：![裁剪](image/README/裁剪.png)
            * 裁剪前頁面內容
            * 點擊後面板出現變化：![儲存（翻頁）面板_裁切](image/README/儲存（翻頁）面板_裁切.png)
                * 紅色框框：代表裁切範圍，可以拖動調整範圍
                * 綠色勾勾：![確認裁剪](image/README/確認裁剪.png)
                    * 調整好範圍後點擊可以完成裁剪
                * 紅色叉叉：![取消裁剪](image/README/取消裁剪.png)
                    * 點擊後退出裁剪
                * 裁切此頁/裁切全部：![裁切此頁](image/README/裁切此頁.png) ![裁切全部：](image/README/裁切全部.png)
                    * 點擊進行切換
                    * 裁切此頁：只裁切當前頁面
                    * 裁切全部：對所有**大小相同**的頁面進行等同於當紅色框框範圍的裁切
            * 為避免調整裁剪範圍時誤觸，點擊裁切按鈕後會自動將當前使用的白板工具切至滑鼠，且若是切換為滑鼠以外的工具，會自行退出裁剪

        * 左移：![左移](image/README/左移.png)
            * 將當前頁面的內容向左（前）移動
        
        * 右移：![右移](image/README/右移.png)
            * 將當前頁面的內容向右（後）移動
        
        * 複製：![複製](image/README/複製.png)
            * 複製當前頁面
        
        * 刪除：![刪除當前頁面](image/README/刪除當前頁面.png)
            * 刪除當前頁面

        * 載入：![載入](image/README/載入.png) 
            * 載入儲存的.json檔案

        * 匯出：![匯出](image/README/匯出.png)
            * 匯出當前儲存（翻頁）面板內的所有內容
            * 點擊後出現可選項：![儲存格式](image/README/儲存格式.png)
            * PDF：儲存成PDF檔案，此後無法讀取
            * JSON：儲存成JSON檔案，可以重複讀取
        * 關閉：![關閉儲存頁面](image/README/關閉儲存頁面.png)
            * 關閉面板

## Feature

- 透明白板
    * 透明的畫布，可以在白板範圍內的任何想要的地方做筆記
    * 功能展示：
        * 畫筆
            * [![Google-meet Parasite 互動式透明白板 - 畫筆demo](https://img.youtube.com/vi/9bihaETWguo/maxresdefault.jpg)](https://youtu.be/9bihaETWguo)
        
        * 輸入文字
            * [![Google-meet Parasite 互動式透明白板 - 輸入文字demo](https://img.youtube.com/vi/ZPmFDrFTtIs/maxresdefault.jpg)](https://youtu.be/ZPmFDrFTtIs)

        
        * 圖案
            * 橢圓
                * [![Google-meet Parasite 互動式透明白板 - 橢圓demo](https://img.youtube.com/vi/9YRnrlS2caI/maxresdefault.jpg)](https://youtu.be/9YRnrlS2caI)

            * 矩型
                * [![Google-meet Parasite 互動式透明白板 - 矩型demo](https://img.youtube.com/vi/kKC-5Xtp6kk/maxresdefault.jpg)](https://youtu.be/kKC-5Xtp6kk)

            * 直線
                * [![Google-meet Parasite 互動式透明白板 - 直線demo](https://img.youtube.com/vi/tRglK5DBk_8/maxresdefault.jpg)](https://youtu.be/tRglK5DBk_8)
        
        * 橡皮擦
            * [![Google-meet Parasite 互動式透明白板 - 橡皮擦demo](https://img.youtube.com/vi/BbUR_xQjYUU/maxresdefault.jpg)](https://youtu.be/BbUR_xQjYUU)
        
        * 顏色選擇
            * [![Google-meet Parasite 互動式透明白板 - 顏色選擇demo](https://img.youtube.com/vi/g742fd0Njdo/maxresdefault.jpg)](https://youtu.be/g742fd0Njdo)
        
        * 粗細選擇
            * [![Google-meet Parasite 互動式透明白板 - 粗細選擇demo](https://img.youtube.com/vi/M98Y8fPCFgc/maxresdefault.jpg)](https://youtu.be/M98Y8fPCFgc)
        
        * 虛線
            * [![Google-meet Parasite 互動式透明白板 - 虛線demo](https://img.youtube.com/vi/AiOGvYlBGYk/maxresdefault.jpg)](https://youtu.be/AiOGvYlBGYk)
        
        * 連線功能
            * 聽眾
                * 編輯自己的白板
                * 編輯講者的白板
        
            * 講者
                * 接受其他人的編輯
                * 屏蔽其他人的編輯
            * [![Google-meet Parasite 互動式透明白板 - 連線功能demo](https://img.youtube.com/vi/dOVXdqidGts/maxresdefault.jpg)](https://youtu.be/dOVXdqidGts)

    * 模式
        * 無白板模式
            * 當前無人分享畫面，白板功能無法使用
    
        * 聽眾模式
            * 當前正在觀看他人分享的畫面，可以在他人分享的畫面上使用白板
    
        * 講者模式
            * 當前正在分享螢幕畫面給他人，整個螢幕都是白板（可讓他人編輯白板的功能限於分享全螢幕）
            [![Google-meet Parasite 互動式透明白板 - 連線功能demo](https://img.youtube.com/vi/bFUolAyBYfk/maxresdefault.jpg)](https://youtu.be/bFUolAyBYfk)
        * 注意事項
            * 當模式切換時在Parasite的UI完成對應的變動前請勿將Google Meet最小化

- 彈幕

  1. 點選彈幕按鈕後，右側會出現三個按鈕(表情符號(尚未完成)、發送彈幕訊息、選擇發送人員)
     ![1719984777800](image/README/1719984777800.png)
     ![1719984795285](image/README/1719984795285.png)

  2. 點選第二個按鈕，會出現輸入框，再輸入完成後，可以選擇是否匿名發言，按下發送後，就會將訊息傳送給其他使用者，在對方的螢幕上就會有彈幕訊息飄過。
     ![1719984817647](image/README/1719984817647.png)
     ![1719984832474](image/README/1719984832474.png)

  3. 點選地三個按鈕，會出現這個會議室的人員(有裝 Parasite 並且連線到 server 的使用者都會出現在這裡)，可以勾選想要發送彈幕訊息的人，這樣彈幕就只會發送給指定使用者。
     ![1719984870227](image/README/1719984870227.png)
     ![1719984883613](image/README/1719984883613.png)

  - 彈幕 demo 影片
    [![Google-meet Parasite 互動式透明白板 - 彈幕demo](https://img.youtube.com/vi/1A1PEL5SByI/maxresdefault.jpg)](https://youtu.be/1A1PEL5SByI)
