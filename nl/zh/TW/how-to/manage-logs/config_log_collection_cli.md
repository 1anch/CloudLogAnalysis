---

copyright:
  years: 2017
lastupdated: "2017-07-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 配置日誌收集 CLI
{: #config_log_collection_cli}

{{site.data.keyword.loganalysisshort}} 服務包括指令行介面 (CLI)，可用來管理雲端中的日誌。CLI 是 Cloud Foundry (CF) 外掛程式。您可以使用指令來檢視日誌的狀態、下載日誌，以及配置日誌保留原則。CLI 提供不同類型的說明：瞭解 CLI 及所支援指令的一般說明、瞭解如何使用指令的指令說明，或瞭解如何使用指令之次指令的次指令說明。
{:shortdesc}


## 安裝日誌收集 CLI
{: #install_cli}

若要安裝日誌收集 CLI，請完成下列步驟：

1. 確認系統中可使用 CF CLI。 

    如需相關資訊，請參閱[必要條件](/docs/services/CloudLogAnalysis/how-to/manage-logs/config_log_collection_cli.html#pre_req)。

2. 安裝日誌收集 CF 外掛程式：

    * 若為 Linux，請參閱[在 Linux 上安裝日誌收集 CLI](/docs/services/CloudLogAnalysis/how-to/manage-logs/config_log_collection_cli.html#install_cli_linux)。
    * 若為 Windows，請參閱[在 Windows 上安裝日誌收集 CLI](/docs/services/CloudLogAnalysis/how-to/manage-logs/config_log_collection_cli.html#install_cli_windows)。
    * 若為 Mac OS X，請參閱[在 Mac OS X 上安裝日誌收集 CLI](/docs/services/CloudLogAnalysis/how-to/manage-logs/config_log_collection_cli.html#install_cli_mac)。
 

## 必要條件
{: #pre_req}

日誌收集 CLI 是一個 CF 外掛程式。您需要先考量下列情境，才能安裝它：

* 您是第一次安裝 CF CLI：

     安裝 CF 外掛程式。如需相關資訊，請參閱[安裝 cf CLI ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html "外部鏈結圖示"){: new_window}。 

* 您已安裝 {{site.data.keyword.Bluemix_notm}} CLI 套件：

    CF CLI 搭載於 {{site.data.keyword.Bluemix_notm}} CLI 套件。

* 您將需要 {{site.data.keyword.Bluemix_notm}} CLI 才能管理其他 Cloud 資源：  

    安裝 {{site.data.keyword.Bluemix_notm}} CLI 套件，請參閱[安裝 {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/bluemix_cli/index.html#install_bluemix_cli)。

然後，驗證 CF 外掛程式可用。在系統的階段作業中，執行下列指令：
    
```
cf -v
```
{: codeblock}
    
輸出如下所示：
    
```
cf version 6.25.0+787326d.2017-02-28
```
{: screen}

**附註：**不能混合使用 {{site.data.keyword.Bluemix_notm}} CLI 指令（亦即 `bx` 指令）和 CF CLI 指令（亦即 `cf` 指令）。



	
## 在 Linux 上安裝日誌收集 CLI
{: #install_cli_linux}

請完成下列步驟，以在 Linux 上安裝日誌收集 CF 外掛程式：

1. 安裝日誌收集 CLI 外掛程式。

    1. 從 [Bluemix CLI 頁面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)，下載 {{site.data.keyword.loganalysisshort}} 服務 CLI 外掛程式的最新版本。 
	
		選取平台值：**linux64**。按一下**儲存檔案**。 
    
    2. 解壓縮外掛程式。
    
        例如，若要在 Ubuntu 中解壓縮 `logging-cli-linux64.gz` 外掛程式，請執行下列指令：
        
        ```
        gunzip logging-cli-linux64.gz
        ```
        {: codeblock}

    3. 將檔案設為可執行檔。
    
        例如，若要將檔案 `logging-cli-linux64` 設為可執行檔，請執行下列指令：
        
        ```
        chmod a+x logging-cli-linux64
        ```
        {: codeblock}

    4. 安裝記載 CF 外掛程式。
    
        例如，若要將檔案 `logging-cli-linux64` 設為可執行檔，請執行下列指令：
        
        ```
        cf install-plugin -f logging-cli-linux64
        ```
        {: codeblock}

2. 設定環境變數 **LANG**。

    如果 CF 不支援您的系統語言環境，請將 *LANG* 設為預設值：*en_US.UTF-8*。如需 CF 所支援語言環境的相關資訊，請參閱[開始使用 cf CLI ![外部鏈結圖示](../../../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.cloudfoundry.org/cf-cli/getting-started.html "外部鏈結圖示"){: new_window}
	
	例如，在 Ubuntu 系統中，編輯 *~/.bashrc* 檔案，然後輸入下列這幾行：
    
    ```
    # add entry for logging CLI
    export LANG = en_US.UTF-8
    ```
    {: codeblock}
    
    開啟新的終端機視窗，然後執行下列指令來驗證已設定變數 LANG 及 LOGGING_ENDPOINT：
    
    ```
    $echo LANG
    en_US.UTF-8
    ```
    {: screen}   
    
3. 驗證記載 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    cf logging --version
    ```
    {: codeblock}
    
    輸出如下所示：
   
    ```
    cf logging version 0.3.5
    ```
    {: screen}


## 在 Windows 上安裝日誌收集 CLI
{: #install_cli_windows}

請完成下列步驟，以在 Windows 上安裝日誌收集 CF 外掛程式：

1. 從 [Bluemix CLI 頁面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)，下載 {{site.data.keyword.loganalysisshort}} 服務 CLI 外掛程式的最新版本。 
	
	1. 選取平台值：**win64**。 
	2. 按一下**儲存檔案**。  
    
2. 執行 **cf install-plugin** 指令，以在 Windows 上安裝日誌收集外掛程式。 

	```
	cf install-plugin PluginName
	```
	{: codeblock}
	
	其中 *PluginName* 是您已下載的檔案名稱。
	
    例如，若要安裝外掛程式 *logging-cli-win64_v1.0.1*，請從終端機視窗執行下列指令：
	
	```
	cf install-plugin logging-cli-win64_v1.0.1.exe
	```
	{: codeblock}
	
    已安裝外掛程式之後，您會收到下列訊息：`Plugin IBM-Logging 1.0.1 successfully installed.`

3. 驗證記載 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    cf logging --version
    ```
    {: codeblock}
    
    輸出如下所示：
   
    ```
    cf logging version 1.0.1
    ```
    {: screen}
	

## 在 Mac OS X 上安裝日誌收集 CLI
{: #install_cli_mac}

請完成下列步驟，以在 Mac OS X 上安裝日誌收集 CF 外掛程式：

1. 從 [Bluemix CLI 頁面](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins)，下載 {{site.data.keyword.loganalysisshort}} 服務 CLI 外掛程式的最新版本。 
	
	1. 選取平台值：**osx**。 
	2. 按一下**儲存檔案**。  
    
2. 執行 **cf install-plugin** 指令，以在 Mac OS X 上安裝日誌收集外掛程式。 

	```
	cf install-plugin PluginName
	```
	{: codeblock}
	
	其中 *PluginName* 是您已下載的檔案名稱。
	
    例如，若要安裝外掛程式 *logging-cli-darwin_v1.0.1*，請從終端機執行下列指令：
	
	```
	cf install-plugin logging-cli-darwin_v1.0.1
	```
	{: codeblock}
	
    已安裝外掛程式之後，您會收到下列訊息：`Plugin IBM-Logging 1.0.1 successfully installed.`

3. 驗證記載 CLI 外掛程式的安裝。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    cf logging --version
    ```
    {: codeblock}
    
    輸出如下所示：
   
    ```
    cf logging version 1.0.1
    ```
    {: screen}
	
	
## 解除安裝日誌收集 CLI
{: #uninstall_cli}

若要解除安裝記載 CLI，請刪除外掛程式。
{:shortdesc}

請完成下列步驟，以解除安裝 {{site.data.keyword.loganalysisshort}} 服務 CLI：

1. 驗證所安裝之記載 CLI 外掛程式的版本。
  
    例如，檢查外掛程式的版本。執行下列指令：
    
    ```
    cf plugins
    ```
    {: codeblock}
    
    輸出如下所示：
   
    ```
    Listing Installed Plugins...
    OK

    Plugin Name   Version   Command Name   Command Help
    IBM-Logging   1.0.1     logging        IBM Logging plug-in
    ```
    {: screen}
    
2. 如果已安裝外掛程式，請執行 `cf uninstall-plugin` 來解除安裝記載 CLI 外掛程式。

    執行下列指令：
        
    ```
    cf uninstall-plugin IBM-Logging
    ```
    {: codeblock}
  

## 取得一般說明
{: #general_cli_help}

若要取得有關 CLI 及所支援指令的一般資訊，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    例如，若要登入「美國南部」地區，請執行下列指令：
	
    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 列出所支援指令及 CLI 的相關資訊。執行下列指令：

    ```
    cf logging help 
    ```
    {: codeblock}
    
    

## 取得指令的說明
{: #command_cli_help}

若要取得如何使用指令的說明，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    例如，若要登入「美國南部」地區，請執行下列指令：
	
    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 取得所支援指令的清單，並識別您需要的指令。執行下列指令：

    ```
    cf logging help 
    ```
    {: codeblock}

3. 取得指令的說明。執行下列指令：

    ```
    cf logging help *Command*
    ```
    {: codeblock}
    
    其中 *Command* 是 CLI 指令的名稱，例如，*status*。



## 取得次指令的說明
{: #subcommand_cli_help}

指令可以有次指令。若要取得次指令的說明，請完成下列步驟：

1. 登入 {{site.data.keyword.Bluemix_notm}} 地區、組織及空間。 

    例如，若要登入「美國南部」地區，請執行下列指令：
	
    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}
    
2. 取得所支援指令的清單，並識別您需要的指令。執行下列指令：

    ```
    cf logging help 
    ```
    {: codeblock}

3. 取得指令的說明，並識別所支援的次指令。執行下列指令：

    ```
    cf logging help *Command*
    ```
    {: codeblock}
    
    其中 *Command* 是 CLI 指令的名稱，例如，*session*。

4. 取得指令的說明，並識別所支援的次指令。執行下列指令：

    ```
    cf logging *Command* help *Subcommand*
    ```
    {: codeblock}
    
    其中 
    
    * *Command* 是 CLI 指令的名稱，例如，*status*。
    * *Subcommand* 是所支援次指令的名稱，例如，指令 *session* 的有效次指令是 *list*。




