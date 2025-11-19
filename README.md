# Web-of-Science-爬蟲 

自動化批次匯出 Web of Science (WOS) 文獻資料的 Selenium Bot

本專案使用 Python + Selenium，透過瀏覽器自動化方式批次下載 Web of Science 的 Excel 文獻檔案。
由於 WOS 每次最多只能匯出 1000 筆，因此本程式會自動執行多輪分批匯出、偵測下載完成、重新命名檔案並持續進行直到所有資料都下載完成。

功能特色

自動填入起訖記錄 (records from / to)

自動點擊 Export → Excel → Export 按鈕

自動等待下載完成（偵測 .crdownload）

已下載筆數為檔案名（避免覆蓋或衝突）
例如: 下載5000筆其檔名為1_1000、1001_2000...

失敗自動重新嘗試，防 Timeout / StaleElement

可長時間運行，完全無人值守

支援大量資料（> 600,000 筆）分批下載

# 使用版本
Python：3.14.0
Selenium：4.38.0
# 使用方式
需先手動下載ChromeDriver不然會超卡

查看 Chrome 版本
搜尋 chrome://version/ 
確認版本後手動下載 ChromeDriver： 

https://googlechromelabs.github.io/chrome-for-testing/

ChromeDriver.py測試 可執行代表沒問題


接著使用wos.crawler.py
只需更改網址BASE_URL 和 抓取筆數TOTAL_N 即可執行

test.py為確認筆數是否抓正確

#小BUG

少數時候檔名沒被改到，是因為程式是靠「下載前後的檔案差異」來判斷新檔案；如果下載完成得太快，導致在拍「之前的列表」時，新檔案其實已經存在，就偵測不到變化，檔名就不會被改。







