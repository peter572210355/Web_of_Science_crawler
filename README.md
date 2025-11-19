# Web-of-Science-爬蟲 
自動化批次匯出 Web of Science (WOS) 文獻資料的 Selenium Bot

本專案使用 Python + Selenium，透過瀏覽器自動化方式批次下載 Web of Science 的 Excel 文獻檔案。
由於 WOS 每次最多只能匯出 1000 筆，因此本程式會自動執行多輪分批匯出、偵測下載完成、重新命名檔案並持續進行直到所有資料都下載完成。

功能特色

自動填入起訖記錄 (records from / to)

自動點擊 Export → Excel → Export 按鈕

自動等待下載完成（偵測 .crdownload）

自動重新命名下載檔案（避免覆蓋或衝突）

失敗自動重新嘗試，防 Timeout / StaleElement

可長時間運行，完全無人值守

支援大量資料（> 600,000 筆）分批下載
