# Web-of-Science-Crawler

Automated batch export of Web of Science (WOS) (URL: https://www.webofscience.com/wos/woscc/smart-search
) literature data using Selenium Bot.

This project uses Python + Selenium to batch download Web of Science Excel files through browser automation.
Since WOS can export up to 1000 records at a time, this program automatically performs multiple batch exports, detects download completion, renames the files, and continues until all records are downloaded.

# Features

Automatically fills in the start and end records (records from / to)

Automatically clicks Export → Excel → Records from: → Record Content: Export → button

Automatically waits for the download to complete (detects .crdownload)

Downloaded record ranges are used as filenames (to avoid overwrite or conflicts)
Example: If 5000 records are downloaded, filenames will be 1_1000, 1001_2000…

Automatically retries on failure, prevents Timeout / StaleElement

Can run for a long time without manual intervention

Supports large-scale data (> 600,000 records) batch export

# Versions Used

Python: 3.14.0
Selenium: 4.38.0

# Usage

You must manually download ChromeDriver first, otherwise the process will be extremely slow.

Check Chrome version
Search chrome://version/
After confirming the version, manually download ChromeDriver:

https://googlechromelabs.github.io/chrome-for-testing/

Run ChromeDriver.py to test. If it runs, then it is correct.

Then use wos.crawler.py
You only need to modify BASE_URL and TOTAL_N (total records to fetch) to execute.

test.py is used to confirm whether the number of records is captured correctly.

Note: Any part containing a path location must be modified to your own path.

# Small BUG

Sometimes a filename is not renamed because the program determines the new file based on the difference before and after download;
if the download completes too fast, the new file already exists when taking the “before” snapshot, making the program unable to detect it, so the filename will not be changed.

It is recommended to keep the batch size under 50,000.

# Note

This is specifically for automating:
Export → Excel → Records from: 1 to TOTAL_N → Record Content: Full Record → Export button

(Example URL: https://www.webofscience.com/wos/woscc/summary/e5e64c73-cc6f-4d8f-9f54-37d62495a2f3-018a0b4503/relevance/1
)
If there are other similar operations, you may modify wos.crawler.py accordingly.

# Web-of-Science-爬蟲 

自動化批次匯出 Web of Science (WOS) (網址:https://www.webofscience.com/wos/woscc/smart-search) 文獻資料的 Selenium Bot

本專案使用 Python + Selenium，透過瀏覽器自動化方式批次下載 Web of Science 的 Excel 文獻檔案。
由於 WOS 每次最多只能匯出 1000 筆，因此本程式會自動執行多輪分批匯出、偵測下載完成、重新命名檔案並持續進行直到所有資料都下載完成。

功能特色

自動填入起訖記錄 (records from / to)

自動點擊 Export → Excel → Records from: → Record Content: Export → 按鈕

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

注意:以上部分有路徑位置請修改自己的路徑

#小BUG

少數時候檔名沒被改到，是因為程式是靠「下載前後的檔案差異」來判斷新檔案；如果下載完成得太快，導致在載「之前的列表」時，新檔案其實已經存在，就偵測不到變化，檔名就不會被改。

建議載入筆數五萬內。

#注意

此為針對自動點擊 Export → Excel → Records from: 1 to TOTAL_N → Record Content: Full Record →  Export 按鈕

(範例網址:https://www.webofscience.com/wos/woscc/summary/e5e64c73-cc6f-4d8f-9f54-37d62495a2f3-018a0b4503/relevance/1)
如有其他類似操作可拿wos.crawler.py做更改







