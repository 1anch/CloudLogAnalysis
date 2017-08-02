---

copyright:
  years: 2017

lastupdated: "2017-07-19"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# 使用 Kibana 執行進階日誌分析
{:#analyzing_logs_Kibana}

在 {{site.data.keyword.Bluemix}} 中，您可以使用 Kibana 5.1（一種開放程式碼分析與視覺化平台），在各種圖形（例如圖表和表格）中監視、搜尋、分析及視覺化您的資料。使用 Kibana 來執行進階分析作業。
{:shortdesc}

Kibana 是一種以瀏覽器為基礎的介面，您可以在這裡以互動方式分析資料及自訂儀表板，然後可以使用該儀表板來分析日誌資料，以及執行進階管理作業。如需相關資訊，請參閱 [Kibana User Guide ![外部鏈結圖示](../../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.elastic.co/guide/en/kibana/5.1/index.html "外部鏈結圖示"){: new_window}。

Kibana 頁面顯示的資料受搜尋限制。預設資料集是由預先配置的索引型樣來定義。若要過濾資訊，您可以新增搜尋查詢，並將過濾器套用至預設資料集。然後，您可以儲存搜尋，以供日後重複使用。 

Kibana 包括可用來分析日誌的不同頁面：

| Kibana 頁面 | 說明 |
|-------------|-------------|
| 探索 | 請利用這個頁面來定義搜尋，並可透過表格及直方圖，以互動方式分析日誌。|
| 視覺化 | 請利用這個頁面來建立圖形及表格等視覺效果，讓您可以用來分析日誌資料及比較結果。|
| 儀表板 | 請利用這個頁面，透過已儲存的視覺效果及搜尋集合來分析日誌。|
{: caption="表 1. Kibana 頁面" caption-side="top"}

**附註：**儘管可以回溯 3 天，但透過「視覺化」頁面或「儀表板」頁面，您一次只能分析 1 整天的資料。依預設，日誌資料會儲存 3 天。 

| Kibana 頁面 | 時段資訊 |
|-------------|-------------------------|
| 探索 | 最多可分析 3 天的資料。|
| 視覺化 | 分析 24 小時內的資料。<br> 您可以過濾歷時 24 小時自訂時段的日誌資料。|
| 儀表板 | 分析 24 小時內的資料。<br> 您可以過濾歷時 24 小時自訂時段的日誌資料。<br> 您設定的時間選取器會套用至內含在儀表板中的所有視覺效果。|
{: caption="表 2. 時段資訊" caption-side="top"}

例如，以下示範如何使用 Kibana，透過不同頁面來顯示空間中的 CF 應用程式或容器相關資訊：

## 導覽至 Kibana 儀表板
{: #launch_Kibana}

您可以使用下列任何方式來啟動 Kibana：

* 從 {{site.data.keyword.loganalysisshort}} 服務儀表板

    您可以啟動 Kibana，讓您看到的資料從所提供之 {{site.data.keyword.Bluemix_notm}} 空間內的服務聚集日誌。
	
	如需相關資訊，請參閱[從 Log Analysis 服務儀表板導覽至 Kibana](/docs/services/CloudLogAnalysis/kibana/launch.html#launch_Kibana_from_log_analysis)。

* 從 {{site.data.keyword.Bluemix_notm}}

    在 Kibana 中，您可以在特定 CF 應用程式的環境定義內，啟動至該特定應用程式的日誌。如需相關資訊，請參閱[從 CF 應用程式儀表板導覽至 Kibana](/docs/services/CloudLogAnalysis/kibana/launch.html#launch_Kibana_from_cf_app)。
    
    在 Kibana 中，您可以在特定 Docker 容器的環境定義內，啟動至該特定容器的日誌。此特性只適用於 {{site.data.keyword.Bluemix_notm}} 所管理雲端基礎架構中部署的容器。如需相關資訊，請參閱[從容器儀表板導覽至 Kibana](/docs/services/CloudLogAnalysis/kibana/launch.html#launch_Kibana_for_containers)。
    
    若為 CF 應用程式，用來過濾 Kibana 中可分析資料的查詢，會擷取 Cloud Foundry 應用程式的日誌項目。Kibana 依預設顯示的日誌資訊，全都與單一 Cloud Foundry 應用程式及其所有實例相關。 
    
    若為容器，用來過濾 Kibana 中可分析資料的查詢，會擷取所有容器實例的日誌項目。Kibana 依預設顯示的日誌資訊，全都與單一容器或容器群組及其所有實例相關。 
    
    

* 從直接瀏覽器鏈結

    您可能會想要啟動 Kibana，讓您看到的資料從所提供之 {{site.data.keyword.Bluemix_notm}} 空間內的服務聚集日誌。
    
    用來過濾儀表板顯示資料的查詢，會擷取 {{site.data.keyword.Bluemix_notm}} 組織中某個空間的日誌項目。Kibana 顯示的日誌資訊，包括部署在 {{site.data.keyword.Bluemix_notm}} 組織中您登入之空間內的所有資源記錄。 
    
    如需相關資訊，請參閱[從 Web 瀏覽器導覽至 Kibana 儀表板](/docs/services/CloudLogAnalysis/kibana/launch.html#launch_Kibana_from_browser)。
    
    

## 以互動方式分析資料
{: #analyze_discover}

在「探索」頁面中，您可以定義新的搜尋查詢，並依查詢來套用過濾器。日誌資料會透過表格及直方圖來顯示。您可以使用這些視覺效果，以互動方式來分析資料。如需相關資訊，請參閱[在 Kibana 中以互動方式分析日誌](analize_logs_interactively.html#analize_logs_interactively)。

您可以從日誌欄位（例如 message_type 及 instance_ID）配置過濾器，並設定時段。您可以動態啟用或停用這些過濾器。表格及直方圖將會顯示符合您啟用之查詢和過濾準則的日誌項目。如需相關資訊，請參閱[在 Kibana 中過濾日誌](/docs/services/CloudLogAnalysis/kibana/filter_logs.html#filter_logs)。

## 透過視覺效果分析資料
{: #analyze_visualize}
    
在「視覺化」頁面中，您可以定義新的搜尋查詢及視覺效果。您也可以開啟已儲存的視覺效果，或儲存視覺效果。

若要分析資料，您可以根據現有搜尋或新搜尋來建立視覺效果。Kibana 包括可用來分析資訊的各種視覺效果類型，例如表格、趨勢及直方圖。每一種視覺效果的目標都不同。部分視覺效果會分組成數列，以提供一個以上查詢的結果。其他視覺效果則會顯示文件或自訂資訊。視覺效果中的資料可以是固定的，也可以在更新搜尋查詢時變更。您可以將視覺效果內嵌在網頁中或予以共用。 

如需相關資訊，請參閱[使用視覺效果來分析日誌](/docs/services/CloudLogAnalysis/kibana/kibana_visualizations.html#kibana_visualizations)。

## 在儀表板中分析資料
{: #analyze_dashboard}

在「儀表板」頁面中，您可以同步自訂、儲存及共用多個視覺效果和搜尋。 

您可以新增、移除及重新排列儀表板中的視覺效果。如需相關資訊，請參閱[在 Kibana 中透過儀表板來分析日誌](/docs/services/CloudLogAnalysis/kibana/analize_logs_dashboard.html#analize_logs_dashboard)。
    
自訂 Kibana 儀表板之後，您可以透過其視覺效果來分析資料，並可儲存起來以供日後重複使用。如需相關資訊，請參閱[儲存 Kibana 儀表板](/docs/services/CloudLogAnalysis/kibana/analize_logs_dashboard.html#save)。

Kibana 中也有**管理**頁面，可讓您用來配置 Kibana，以及儲存、刪除、匯出和匯入搜尋、視覺效果和儀表板。

