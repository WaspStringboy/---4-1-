# 南華大學軟體工程-利用"4+1"視圖建模方法進行"精準扶貧管理系統"的軟件架構設計
11124115 徐言宏 11124131 陳毅倫
```
目錄
 1 “4+1”視圖建模方法
 2 利用「4+1」視圖建模方法進行「精準扶貧管理系統」的軟體架構設計流程
 2.1 精準扶貧管理系統內容描述
 2.2 需求分析
 2.2.1 角色分類
 2.2.2 系統需求分析
 2.2.3 功能模組圖
 2.3場景視圖用例圖設計建模
 2.3.1精準扶貧管理系統用例圖
 2.3.2 精準扶貧管理系統關鍵用例描述
 2.4 邏輯試圖之類圖設計建模
 2.4.1 精準扶貧管理系統實體及其屬性分析
 2.4.2 精準扶貧管理系統邏輯視圖-類別圖
 2.4.3 精準扶貧管理系統關鍵類別圖說明
 2.5 開發視圖建模
 2.5.1 包圖設計建模
 2.5.2 組件圖設計建模
 2.6 過程視圖之交互圖建模
 2.6.1 註冊用戶順序圖
 2.6.2提交申請順序圖
 2.6.3查看貧困戶檔案順序圖
 2.6.4查詢公告順序圖
 2.6.5 查詢系統資料資訊順序圖
 2.7物理視圖之部署圖建模
 3 利用設計模式改進
 3.1 訊息通知模組管理模組的原設計方案類別圖
 3.2訊息通知模組管理模組採用工廠方法模型設計方案類別圖
 3.3設計模式改進前後比較分析
 4 總結
 4.1內容總結
 4.2工作總結
 原文連結： https://blog.csdn.net/NGUever15/article/details/71353168
```
# 1 “4+1”視圖建模方法
```
 軟體架構常用模型就是視圖模型，類似RM-ODP的視點模型，可以從多個角度描述一個複雜的軟體系統。
最受歡迎的視圖模型就是「4+1」視圖模型，它由五個視圖組成，包括場景視圖、邏輯視圖、流程視圖、實體視圖和開發視圖，如圖1-1所示。
我們可以粗略地把“4+1”視圖模型看成是參考軟體生命週期五個階段建立的視圖模型，雖然實際上每個視圖描述的內容並不是局限於生命週期的一個階段
，但顯而易見的是 ，除了結構要素之外，這種視圖模型也包含了流程要素。
```
![image](https://github.com/WaspStringboy/---4-1-/blob/main/1-1.png)
```
“4+1”視圖模型實際上使得有不同需求的人員能夠得到他們對於軟體體系結構想要了解的東西。 
系統工程師先從實體視圖，然後從流程視圖靠近體系結構。 
最終使用者、客戶、資料專家從邏輯視圖看體系結構；專案經理、軟體配置人員從開發視圖看體系結構。
邏輯視圖也稱為概念視圖，主要是支援系統功能需求的抽象描述，即係統最終將提供給使用者什麼樣的服務。 
邏輯視圖關注的是系統必須為使用者提供的功能，不僅包括使用者可見的功能，還包括為實現使用者功能而必須提供的系統功能。 
在UML中，邏輯視圖包含了類別、介面和協作，它展現了系統的靜態或結構組成及特徵，描述場景視圖提出的系統功能的實現。 
邏輯視圖在UML中通常表現為類別圖、交互圖、順序圖和狀態圖。
 開發視圖也稱為模組視圖，主要著重於描述系統的組織，與邏輯視圖密切相關，都描述了系統的靜態結構。
開發視圖關注的是程式包，不僅包括要編寫的原始程序，還包括可以直接使用的第三份SDK和現成框架、類別庫，以及開發的系統將運行於其上的系統軟體或中間件等。
開發視圖關注軟體開發環境下實際模組的組織，反映了開發難度、軟體管理、重複使用性和通用性及由工具集、程式語言所帶來的限制和限制等。 
開發視圖和邏輯視圖之間可能存在一定的映射關係。 
開發視圖在UML中通常表現為包圖。
過程視圖主要著重於描述系統的動態行為，也就是係統運作時所表現出來的相關特性，著重解決系統的可靠性、吞吐量、並發性、分佈性和容錯性。 
過程視圖的關注點是運行中的執行緒、進程和物件等概念，以及相關的並發、同步、通訊等問題。 過程視圖和開發視圖相比，開發視圖一般偏重程式包在編譯時的靜態依賴關係
，而這些程式運行起來之後就會表現為物件、執行緒、進程以及它們之間的呼叫關係，過程視圖比較關心的 正式這些運行時單元的互動問題。
過程視圖在UML中通常表現為活動圖、互動圖和狀態圖。
實體視圖描述如何把系統軟體元素映射到硬體上，通常要考慮系統的效能、規模和容錯等問題，展示了所需的實體環境、硬體配置和分佈狀況。 
實體視圖關注的是目標程式及其依賴的運行庫和系統軟體最終如何安裝和部署到實體機器上，以及如何部署機器和網路來配置軟體系統的可靠性、可擴展性等要求。 
實體視圖和過程視圖相比，過程視圖特別關注目標程式的動態執行情況，而物理視圖重視目標程式的靜態位置問題；物理視圖是綜合考慮軟體系統和整個IT系統相互影響的架構視圖。 
實體視圖在UML中通常表現為部署圖。
```
# 2利用「4+1」視圖建模方法進行「精準扶貧管理系統」的軟體架構設計流程

# 2-1精準扶貧管理系統內容描述
```
精準扶貧資訊化平台可實現全省貧困戶資訊的全面、準確統計；對扶貧計畫、扶貧資金的全面公開、監督管理；對扶貧過程進行有效追蹤、管理；對扶貧結果進行即時查詢；
為扶貧工作 的更進一步進行累積有效的基礎數據，為全省扶貧的大數據趨勢分析奠定良好的基礎。
精準扶貧資訊化平台由精準扶貧管理系統支持，該系統適用於省級、市級扶貧主管部門對扶貧資訊數據的及時準確統計
，扶貧資訊的精準推送，為扶貧工作提供互動溝通的平台，實現對 扶貧工作的資訊化管理。
精準扶貧管理系統主要分為四個部分，精準辨識、精準幫扶／管理、協助成效評估意見回饋及大數據分析。 
個精準扶貧資訊化平台的應用貫穿貧困戶精確識別、精確幫助、精確管理、幫助成效評估、意見回饋、大數據分析等整個扶貧全過程；
在貧困戶精確識別階段可實現扶貧資訊公示、 評選結果回饋、建立貧窮戶檔案及資料庫等功能；在協助階段，可為精確幫助、精確管理提供資訊化手段支撐
，包括貧窮戶資訊管理、 陽光操作管理、扶貧事權管理；在幫助成效評估和意見回饋階段，可提供基於互聯網+的線上評價和網站線上回饋功能；
透過對系統運作累積的大數據進行系統分析，可提供對貧窮原因、 幫助措施、幫助效果、貧窮戶分佈等的關聯性分析，趨勢分析、預測，綜合資料分析
，資料探勘，領導輔助決策，統計報表等功能。 具體內容描述如圖2-1-1所示。
具體來講，基於「精準扶貧資訊化平台」主要包括全省四級一體的數據平台、基於互聯網的外網網站
、各級人員使用的手機APP客戶端、扶貧事權管理系統和扶貧大數據分析系統 等主要內容，並建立對應的資訊化支撐體系。
```
# 2-2需求分析
# 2-2-1角色分類
```
 根據精準扶貧管理系統所有的內容描述，我們可以大致擬定和精準扶貧管理系統有關的角色為以下四種。
序號          名稱          描述                              權限
1            群眾         貧困村民                      1.查看公告通知2.在線提出貧困申請3.在線留言評論4.管理個人基本資料5.查看個人貧困戶檔案

2         基層工作人員    村級幹部或指定的     
                         扶貧工作人員，                 1.新建貧窮戶檔案2.查詢貧窮戶檔案3.更新貧窮戶檔案 4.刪除貧困戶檔案
                         負責群眾檔案管理

3         系統管理員     指定的系統管理人員，
                        依審核結果進行系統訊息管理、     1.發佈公告通知2.處理群眾貧窮申請3.留言評論管理4.使用者管理
                        發佈通知公告及使用者管理

4          主管領導      鎮級以及以上幹部或指定的扶       1.查詢貧困戶檔案2.查看群眾留言評論3.查看扶貧資金發放流程4.查看扶貧過程狀況和進度 5.查看貧困戶資訊資料庫統計分析報表
                        貧工作人員，負責扶貧審查和監督
```
# 2-2-2系統需求分析
```
精準扶貧資訊化平台的應用貫穿貧困戶精確識別、精確幫助、精確管理、幫助成效評估、意見回饋、大數據分析等整個扶貧全過程；
在貧困戶精確識別階段可實現扶貧資訊公示、評選 結果回饋、建立貧困戶檔案和資料庫等功能；
在幫助階段，可為精確幫助、精確管理提供資訊化手段支撐，包括貧困戶資訊管理、陽 光操作管理、扶貧事權管理；在幫助成效評估和意見回饋階段
，可提供基於互聯網+的線上評價和網站線上回饋功能；透過對系統運作累積的大數據進行系統性分析，可提供對貧窮原因、 幫助措施、幫助效果、貧窮戶分佈等的關聯性分析
，趨勢分析、預測，綜合資料分析，資料探勘，領導輔助決策，統計報表等功能。
```
# *精準扶貧管理系統功能性分析
```
精準扶貧管理系統的功能性分析可以反映這個系統所能完成的各項功能，它能夠清楚、明確地把這個系統要完成的功能展示給後續的設計人員和使用者。
精準扶貧管理系統的具體功能如下：
```
```
系統允許群眾註冊。

 系統允許群眾登入系統。

 系統允許群眾查看個人基本資料。

 系統允許群眾修改個人基本資料。

 系統允許群眾在線上提出貧困戶申請。

 系統允許群眾進行線上留言。

 系統允許群眾進行線上評價。

 系統允許群眾查看個人的貧困戶檔案。

 系統為群眾分配自己的帳戶和存取權限。

 系統允許基層工作人員登陸系統。

 系統允許基層工作人員查看群眾使用者基本資訊。

 系統允許基層工作人員新建貧困戶檔案。

 系統允許基層工作人員更新貧窮戶檔案。

 系統允許基層工作人員查詢貧窮戶檔案。

 系統允許基層工作人員刪除貧窮戶檔案。

 系統為基層工作人員分配自己的帳戶和存取權限。

 系統允許系統管理員登入系統。

 系統允許系統管理員管理群眾用戶貧窮申請。

 系統允許系統管理員公告通知「貧困戶」名額。

 系統允許系統管理員公告通知申請評選須知。

 系統允許系統管理員公告通知申請人名單資訊。

 系統允許系統管理員公告通知貧戶評選結果。

 系統允許系統管理員修改公告通知。

 系統允許系統管理員刪除公告通知。

 系統允許系統管理員查看公告通知。

 系統允許系統管理員查看群眾線上留言。

 系統允許系統管理員刪除群眾線上留言。

 系統允許系統管理員回覆群眾線上留言。

 系統允許系統管理員查看群眾線上評論。

 系統允許系統管理員刪除群眾線上評論。

 系統允許系統管理員回覆群眾線上評論。

 系統允許系統管理員查看使用者基本資訊。

 系統允許系統管理員修改使用者基本資訊。

 系統允許系統管理員管理使用者權限。

 系統為系統管理員分配自己的帳戶和存取權限。

 系統允許主管領導登入系統。

 系統允許主管領導查看貧困戶檔案。

 系統允許主管領導查看公告通知。

 系統允許主管領導查看群眾使用者基本資訊。

 系統允許主管領導查看貧困戶資訊資料庫分析統計報表。

 系統允許主管領導查看群眾留言評論。

 系統允許主管領導查看扶貧資金發放流程及進度。

 系統允許主管領導查看扶貧過程和進度。
```
 # *精準扶貧管理系統非功能性分析
```
 網路回應速度應該盡量快。

 用戶填寫的資料應該盡量少，盡量採用選擇和勾選方式。

 系統應該有預留接口，可以方便連接到客服的電話。
```
# 2-2-3功能模組圖
```
精準扶貧管理系統的功能模組圖反映了精準扶貧管理系統的功能及各個功能之間的關係。 
總體分為「註冊」、「登入」、「公告通知」、「檔案管理」、「訊息管理」、「留言回饋」、「使用者管理」、「審查監督」八個模組，具體內容如圖所示 。
```

```
功能模組圖說明：

 註冊
 【功能描述】
 群眾使用者在使用精準扶貧管理系統進行線上貧窮申請、線上留言、線上評論之前，需要進行使用者註冊，並填寫相應的註冊資訊。
 【操作者】群眾

 登入
 【功能描述】
 系統所有用戶，包括群眾、基層工作人員、系統管理員以及主管領導，在本精準扶貧管理系統進行相應權限的操作之前都需要先登入系統，以便系統為其分配操作權限。
 【操作者】群眾、基層工作人員、系統管理員、主管領導

 公告通知
 【功能描述】
 群眾使用者在公告通知面板上瀏覽查看由系統管理員發布最新通知公示資訊。
 【操作者】群眾
 【功能描述】
 系統管理員在公告通知模組新建公告通知，編輯公告通知內容，並發佈到公告通知面板上，供群眾使用者瀏覽查看。
 【操作者】系統管理員

 檔案管理
 【功能描述】
 針對貧窮申請通過的群眾用戶，需要對進行一系列的貧困戶檔案管理， 包括新建貧困戶檔案、查看貧困戶檔案、更新貧困戶檔案、刪除貧困戶檔案的操作
，其中貧困戶檔案中，包含了 貧窮戶基本資料表、貧窮戶需求狀況表、貧窮幫助狀況表、脫貧計畫、貧窮戶台帳、幫助結果、幫助措施等內容。
 【操作者】基層工作人員

 訊息管理
 【功能描述】
 主要針對群眾使用者對精準扶貧管理系統的一系列作業進行回應處理。 包括群眾用戶的貧窮申請、線上評論、線上留言等內容的查看、刪除、回覆等。
 【操作者】系統管理員

 留言回饋
 【功能描述】
 為了達到更好更準確的幫助效果，精準扶貧管理系統為群眾用戶提供了留言回饋功能模組
，群眾用戶可以針對公告通知、幫助措施、幫助結果、幫助成效等內容進行線上留言、線上 評價等操作。
 【操作者】群眾

 使用者管理
 【功能描述】
 精準扶貧管理系統的使用者有四種，系統為每個使用者分配了自己的帳戶和權限，系統管理員可對使用者的信心進行檢視和修改，以及權限的設定。
 【操作者】系統管理員

 審查監管
 【功能描述】
 實現對扶貧資金、扶貧計畫、計畫審批的全流程監管。 充分發揮省、市兩級政府的扶貧資金和計畫監管作用，主管領導可在該功能模組​​下查看扶貧計畫進度
，資金發放情況、扶貧審批情況以及貧困戶資訊資料庫分析統計報表等內容。
 【操作者】主管領導
```
# 2-3場景視圖用例圖設計建模
# 2-3-1精準扶貧管理系統用例圖
```
群眾用例圖、基層工作人員用例圖、系統管理員用例圖、主管領導用例圖分別如圖所示。
```
# 2-3-2精準扶貧管理系統關鍵用例描述
```
用例編號  23201
用例名稱  註冊
主要參與者  群眾
說明  群眾註冊精準扶貧管理系統的帳號
前置條件  無
基本事件流  1. 點擊註冊按鈕跳轉至註冊頁面2. 填寫用戶註冊資訊手機密碼暱稱真實姓名身分證
異常事件流  1、由於網路原因，造成資料操作時報錯，關閉報錯資訊後停留在原來的介面。  
後置條件  在註冊介面顯示使用者註冊成功
```
```
用例編號  23202
用例名稱  登入
主要參與者  群眾、基層工作人員、系統管理員、主管領導
說明  用戶在使用精準扶貧管理系統之前，需要進行用戶登入
前置條件  註冊用戶或系統分配帳戶
基本事件流  1. 點擊 登入按鈕跳轉至登入頁面2. 填寫使用者登入資訊手機號碼密碼3. 點選登入按鈕

           1. 因網路原因，造成資料操作時出錯，關閉報錯資訊後停留在原來的介面。
異常事件流  2. 登入使用者不存在，提示使用者註冊或輸入正確的使用者名，停留該頁面。
           3. 登入使用者存在，密碼輸入錯誤，提示使用者輸入正確的密碼，停留該頁面。 
           
後置條件  顯示登入成功，頁面跳到系統首頁
```
```
用例編號  23203
用例名稱  查看公告通知
主要參與者  群眾、主管領導
說明  在系統首頁瀏覽查看由系統管理員發布的公告通知信息
前置條件  登入系統
基本事件流  1. 瀏覽公告通知清單密碼 2. 點選查看公告通知
異常事件流由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面。
後置條件  跳到公告通知的詳細內容頁面
```
```
用例編號 23204
用例名稱 線上貧窮申請
主要參與者 群眾
說明 使用者在精準扶貧管理系統進行線上貧窮申請
前置條件 登入系統
基本事件流 1. 點選貧窮申請按鈕，跳到申請單填寫頁面 2. 填寫貧窮戶相關資訊以及申請理由 3. 點選提交申請按鈕
異常事件流 由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面。
後置條件 顯示申請提交成功，並跳轉系統首頁
```
```
用例編號 23205
用例名稱 管理個人基本訊息
主要參與者 群眾
說明 群眾使用者可以對註冊用戶時填寫的相關資訊進行管理
前置條件 登入系統
基本事件流 1. 進入個人中心，點選查看個人資料 2. 點選修改個人資料 3. 填寫對應的修改內容 4. 點選儲存修改
異常事件流 由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面上
後置條件 顯示修改成功，並跳轉個人中心
```
```
用例編號 23206
用例名稱 線上留言
主要參與者 群眾
說明 群眾使用者可以對系統公告通知的內容進行線上留言
前置條件 登入系統
基本事件流 1. 點選留言按鈕，彈出留言內容輸入框 2. 輸入留言內容 3. 點選提交按鈕
異常事件流 1. 由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面。2. 留言內容為空，提示使用者留言內容不能為空，且保持留言輸入狀態。
後置條件 顯示留言成功，返回公告通知頁面
```
```
用例編號 23207
用例名稱 線上評論
主要參與者 群眾
說明 群眾使用者可以幫助結果等內容進行網路評論／評價
前置條件 登入系統
基本事件流 1. 點選評論按鈕，彈出評論內容輸入框 2. 輸入評論內容 3. 點選提交按鈕
異常事件流 1. 由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面。2. 評論內容為空，提示使用者評論內容不能為空，且保持評論輸入狀態。
後置條件 顯示評論成功，返回評論內容頁面
```
```
用例編號 23208
用例名稱 新建貧窮戶檔案
主要參與者 基層工作人員
說明 標準錯誤輸出
前置條件 登入系統
基本事件流 1. 進入檔案管理頁面，點選新建貧窮戶檔案 2. 選擇貧窮戶檔案類型並點選新建按鈕 3. 在跳轉的貧窮戶檔案內容頁面錄入貧窮戶對應的資訊 4. 點選儲存按鈕
異常事件流 由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面上
後置條件 顯示新建成功，跳轉檔案管理頁面
```
```
用例編號 23209
使用案例名稱 管理公告通知
主要參與者 系統管理員
說明 系統管理員發布、修改、刪除公告通知等
前置條件 登入系統

基本事件流 1. 進入公告通知頁面，點選新/檢視/修改/刪除公告通知按鈕2. 選擇新公告，編輯公告通知內容，點選發布按鈕3.選擇公告通知點選查看按鈕
          4. 選擇公告通知點選修改 按鈕，輸入修改內容，點選儲存按鈕5. 選擇公告通知點選刪除按鈕

異常事件流 由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面上
後置條件 顯示操作成功，跳轉公告通知頁面
```
```
用例編號 23210
使用案例名稱 管理用戶
主要參與者 系統管理員
說明 系統管理員對系統使用者進行資訊修改、權限設定等管理操作
前置條件 登入系統
基本事件流 1. 進入用戶管理頁面，選擇用戶，點擊管理按鈕 2. 查看用戶基本信息，點擊修改按鈕 3. 輸入修改內容，點擊儲存按鈕 4. 設定用戶權限，點擊儲存按鈕
異常事件流 由於網路原因，造成資料操作時報錯，關閉報錯訊息後停留在原來的介面上
後置條件 顯示操作成功，跳轉使用者管理頁面
```

# 2-4 邏輯試圖之類圖設計建模
# 2-4-1精準扶貧管理系統實體及其屬性分析
```
根據前面的系統用例分析，我們抽象化系統實體，並對實體進行了輸入性分析，實體及其屬性分析圖如圖2.4.1-1所示。
```
# 2-4-2精準扶貧管理系統邏輯視圖-類別圖

# 2-4-3精準扶貧管理系統關鍵類別圖說明

# *訊息資料庫類
```
 由申請單、評論、留言、公告通知組成，包含了公告通知模組、留言回饋模組和訊息管理模組。
 請申請單內容、評論內容、留言內容由群眾使用者產生，並由系統管理員負責管理處理，包含了檢視、刪除、修改等操作。 
通知公告內容由系統管理員產生，群眾使用者可查看。 主管領導可查看訊息資料庫類別中的所有內容。
```
# *貧窮戶資訊資料庫類
```
 由所有審核認證的貧困戶檔案組成，對應了功能模組為檔案管理。 
內容由基層工作人員輸入，並進行管理，包括新建、檢視、修改、刪除等操作。 群眾用戶可查看自己的貧困戶檔案
，主管領導可查看所有的貧困戶檔案。
```
# *使用者資料庫
```
 由所有群眾使用者的基本資訊組成，對應的功能模組為使用者管理。 內容由註冊群眾使用者產生，系統管理員可對內容進行管理
，包括檢視、修改使用者資訊以及設定使用者權限。 基礎工作人員和領導者可查看使用者資料庫內容的使用者基本資訊。
```
# *項目統計資料庫類
```
 由扶貧計畫、扶貧資金以及統計報表組成，對應的功能模組為審查監管。 內容有使用者資料庫、貧窮戶資訊資料庫和訊息資料庫的資料統計產生。 
由主管領導負責管理，包括新建、查看、修改、刪除報表和查看專案及專案資金等等操作。

```
# 2-5
# 2-5-1
```
內容
```
# 2-5-2
```
內容
```
# 2-6
# 2-6-1
```
內容
```
# 2-6-2
```
內容
```
# 2-6-3
```
內容
```
# 2-6-4
```
內容
```
# 2-6-5
```
內容
```
# 2-7
```
內容
```
# 3
# 3-1
```
內容
```
# 3-2
```
內容
```
# 3-3
```
內容
```
# 4
# 4-1
```
內容
```
# 4-2
```
內容
```
