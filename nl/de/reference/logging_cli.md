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

# IBM Cloud Log Analysis - Befehlszeilenschnittstelle
{: #logging_cli}

Die Befehlszeilenschnittstelle von {{site.data.keyword.loganalysislong}} ist ein Plug-in zur Verwaltung der Protokolle für Cloudressourcen, die in einem Bereich einer {{site.data.keyword.Bluemix}}-Organisation ausgeführt werden.
{: shortdesc}

**Voraussetzungen**
* Bevor Sie die Protokollierungsbefehle ausführen, müssen Sie sich bei {{site.data.keyword.Bluemix_notm}} mit dem Befehl `cf login` anmelden, um ein {{site.data.keyword.Bluemix_short}}-Zugriffstoken zu generieren und um Ihre Sitzung zu authentifizieren.

Informationen zur Verwendung der Befehlszeilenschnittstelle von {{site.data.keyword.loganalysisshort}} finden Sie unter [Protokolle verwalten](/docs/services/CloudLogAnalysis/log_analysis_ov.html#log_analysis_ov).

<table>
  <caption>Befehle für die Verwaltung von Protokollen</caption>
  <tr>
    <th>Befehl</th>
    <th>Verwendungszweck</th>
  </tr>
  <tr>
    <td>[cf logging](#base)</td>
    <td>Mit diesem Befehl können Informationen über die Befehlszeilenschnittstelle (CLI) - wie z. B. die Version oder die Liste der Befehle - abgerufen werden.</td>
  </tr>
  <tr>
    <td>[cf logging auth](#auth)</td>
    <td>Verwenden Sie diesen Befehl, um das Protokollierungstoken anzufordern, mit dem Sie Protokolle an den {{site.data.keyword.loganalysisshort}}-Service senden können.</td>
  </tr>
  <tr>
    <td>[cf logging delete](#delete)</td>
    <td>Mit diesem Befehl können Sie Protokolle löschen, die in 'Log Collection' gespeichert sind.</td>
  </tr>
  <tr>
    <td>[cf logging download (Beta)](#download)</td>
    <td>Verwenden Sie diesen Befehl, um Protokolle aus 'Log Collection' in eine lokale Datei herunterzuladen oder um Protokolle an ein anderes Programm (wie z. B. ELK-Stack) umzuleiten. </td>
  </tr>
  <tr>
    <td>[cf logging help](#help)</td>
    <td>Mit diesem Befehl können Sie Hilfeinformationen zur Verwendung der Befehlszeilenschnittstelle und eine Liste aller Befehle abrufen.</td>
  </tr>
  <tr>
    <td>[cf logging option](#option)</td>
    <td>Verwenden Sie diesen Befehl zum Anzeigen oder Festlegen des Aufbewahrungszeitraums für Protokolle, die in einem {{site.data.keyword.Bluemix_notm}}-Bereich oder -Konto verfügbar sind.</td>
  </tr>
  <tr>
    <td>[cf logging session create (Beta)](#session_create)</td>
    <td>Mit diesem Befehl können Sie eine neue Sitzung erstellen.</td>
  <tr>
  <tr>
    <td>[cf logging session delete (Beta)](#session_delete)</td>
    <td>Mit diesem Befehl können Sie eine Sitzung löschen.</td>
  <tr>  
  <tr>
    <td>[cf logging session list (Beta)](#session_list)</td>
    <td>Verwenden Sie diesen Befehl, um die aktiven Sitzungen und die zugehörigen IDs aufzulisten.</td>
  <tr>  
  <tr>
    <td>[cf logging session show (Beta)](#session_show)</td>
    <td>Verwenden Sie diesen Befehl, um den Status einer einzelnen Sitzung anzuzeigen.</td>
  <tr>  
  <tr>
    <td>[cf logging status](#status)</td>
    <td>Verwenden Sie diesen Befehl, um Informationen zu den Protokollen abzurufen, die in einem {{site.data.keyword.Bluemix_notm}}-Bereich oder -Konto erfasst werden.</td>
  </tr>
  </table>


## cf logging
{: #base}

Dieser Befehl stellt Informationen zur Version und Verwendungsweise der Befehlszeilenschnittstelle bereit.

```
cf logging [parameters]
```
{: codeblock}

**Parameter**

<dl>
<dt>--help, -h</dt>
<dd>Legen Sie diesen Parameter fest, um die Liste der Befehle anzuzeigen oder um Hilfeinformationen für einen Befehl anzufordern.
</dd>

<dt>--version, -v</dt>
<dd>Legen Sie diesen Parameter fest, um die Version der Befehlszeilenschnittstelle auszugeben.</dd>
</dl>

**Beispiele**

Um die Liste der Befehle abzurufen, führen Sie den folgenden Befehl aus:

```
cf logging --help
```
{: codeblock}

Um die Version der Befehlszeilenschnittstelle abzurufen, führen Sie den folgenden Befehl aus:

```
cf logging --version
```
{: codeblock}


## cf logging auth
{: #auth}

Dieser Befehl gibt das Protokollierungstoken zurück, mit dem Sie Protokolle an den {{site.data.keyword.loganalysisshort}}-Service senden können. 

**Hinweis:** Das Token ist unbegrenzt gültig.

```
cf logging auth
```
{: codeblock}

**Zurückgegebene Werte**

<dl>
  <dt>Protokollierungstoken</dt>
  <dd>Beispiel: `jec8BmipiEZc`.
  </dd>
  
  <dt>Organisations-ID</dt>
  <dd>GUID der {{site.data.keyword.Bluemix_notm}}-Organisation, bei der Sie angemeldet sind.
  </dd>
  
  <dt>Bereichs-ID</dt>
  <dd>Die GUID des Bereichs in der Organisation, bei der Sie angemeldet sind.
  </dd>
</dl>

## cf logging delete
{: #delete}

Mit diesem Befehl können Sie Protokolle löschen, die in 'Log Collection' gespeichert sind.

```
cf logging delete [Parameter]
```
{: codeblock}

**Parameter**

<dl>
  <dt>--start Wert, -s Wert</dt>
  <dd>(Optional) Legt das Startdatum in koordinierter Weltzeit (UTC) fest: *JJJJ-MM-TT*, z. B. `2006-01-02`. <br>Der Standardwert ist auf 'vor zwei Wochen' festgelegt.
  </dd>
  
  <dt>--end Wert, -e Wert</dt>
  <dd>(Optional) Legt das Enddatum in koordinierter Weltzeit (UTC) fest: *JJJJ-MM-TT*. <br>Die UTC-Format des Datums ist **JJJJ-MM-TT**, z. B. `2006-01-02`. <br>Der Standardwert wird auf das aktuelle Datum gesetzt.
  </dd>
  
  <dt>--type Wert, -t Wert</dt>
  <dd>(Optional) Legt den Protokolltyp fest. <br>Ein Protokolltyp ist beispielsweise *syslog*. <br>Der Standardwert lautet **\** *. <br>Sie können mehrere Protokolltypen angeben, indem Sie die einzelnen Typen durch Kommas trennen. Beispiel: **Protokolltyp_1,Protokolltyp_2,Protokolltyp_3*.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Optional) Legt den Umfang der Protokollinformationen fest, die auf Kontoebene zur Verfügung gestellt werden. <br>Erfolgt keine Angabe für diesen Parameter, werden standardmäßig Informationen zu dem aktuellen Bereich bereitgestellt.
  </dd>
</dl>

**Beispiel**

Führen Sie den folgenden Befehl aus, um die Protokolle des Typs *linux_syslog* für den 25. Mai 2017 zu löschen: 
```
cf logging delete -s 2017-05-25 -e 2017-05-25 -t linux_syslog
```
{: codeblock}



## cf logging download (Beta)
{: #download}

Mit diesem Befehl können Sie Protokolle aus 'Log Collection' in eine lokale Datei herunterladen oder Protokolle an ein anderes Programm (zum Beispiel Elastic Stack) umleiten.  

**Hinweis:** Um Dateien herunterladen zu können, müssen Sie zuerst eine Sitzung erstellen. Eine Sitzung definiert die herunterzuladenden Protokolle abhängig vom Datumsbereich, vom Protokolltyp und vom Kontotyp. Sie laden Protokolle im Kontext einer Sitzung herunter. Weitere Informationen finden Sie unter [cf logging session create (Beta)](/docs/services/CloudLogAnalysis/reference/logging_cli.html#session_create). 

```
cf logging download [Parameter] [Argumente]
```
{: codeblock}

**Parameter**

<dl>
<dt>--output Wert, -o Wert</dt>
<dd>(Optional) Legt den Pfad und den Dateinamen für die lokale Ausgabedatei fest, in die die Protokolle heruntergeladen werden. <br>Der Standardwert ist ein Bindestrich (-). <br>Legen Sie diesen Parameter auf den Standardwert fest, damit die Protokolle an die Standardausgabe ausgegeben werden.</dd>
</dl>

**Argumente**

<dl>
<dt>session_ID</dt>
<dd>Geben Sie hierfür den Wert der Sitzungs-ID an, den Sie erhalten, wenn Sie den Befehl `cf logging session create` ausführen. Dieser Wert gibt an, welche Sitzung beim Herunterladen der Protokolle verwendet werden soll. <br>**Hinweis:** Der Befehl `cf logging session create` enthält die Parameter, die steuern, welche Protokolle heruntergeladen werden. </dd>
</dl>

**Hinweis:** Wenn der Download abgeschlossen ist, hat ein nochmaliges Ausführen desselben Befehls keinerlei Auswirkung. Um dieselben Daten erneut herunterzuladen, müssen Sie eine andere Datei oder eine andere Sitzung verwenden.

**Beispiele**

Um Protokolle in eine Datei mit dem Namen mylogs.gz herunterzuladen, führen Sie den folgenden Befehl aus:

```
cf logging download -o mylogs.gz guBeZTIuYtreOPi-WMnbUg==
```
{: screen}

Führen Sie den folgenden Befehl aus, um Protokolle in eine eigene Elastic Stack-Instanz herunterzuladen: 

```
cf logging download guBeZTIuYtreOPi-WMnbUg== | gunzip | logstash -f logstash.conf
```
{: screen}

Die folgende Datei ist ein Beispiel für eine Datei logstash.conf:

```
input {
  stdin {
    codec => json_lines {}
  }
}
output {
  elasticsearch {
    hosts => [ "127.0.0.1:9200" ]
  }
}
```
{: screen}


## cf logging help
{: #help}

Dieser Befehl bietet Hinweise zur Verwendung eines Befehls.

```
cf logging help [Parameter]
```
{: codeblock}

**Parameter**

<dl>
<dt>Befehl</dt>
<dd>Geben Sie den Namen des Befehls an, für den Sie Hilfeinformationen abrufen wollen.
</dd>
</dl>


**Beispiele**

Um Hilfeinformationen zu dem Befehl abzurufen, mit dem Sie den Status von Protokollen anzeigen können, führen Sie den folgenden Befehl aus:

```
cf logging help status
```
{: codeblock}


## cf logging option
{: #option}

Mit diesem Befehl können Sie den Aufbewahrungszeitraum für Protokolle anzeigen oder ändern, die in einem {{site.data.keyword.Bluemix_notm}}-Bereich oder -Konto verfügbar sind. 

* Der Zeitraum wird als eine Anzahl von Tagen festgelegt.
* Der Standardwert ist **-1**.  

**Hinweis:** Standardmäßig werden alle Protokolle gespeichert. Sie müssen sie manuell mit dem Befehl **delete** löschen. Definieren Sie eine Aufbewahrungsrichtlinie zum automatischen Löschen der Protokolle. 

```
cf logging option [Parameter]
```
{: codeblock}

**Parameter**

<dl>
<dt>--retention Wert, -r Wert</dt>
<dd>(Optional) Legt die Aufbewahrungsdauer (Anzahl Tage) fest. <br> Der Standardwert ist 30 Tage.</dd>

<dt>--at-account-level, -a </dt>
  <dd>(Optional) Legt den Geltungsbereich auf Kontoebene fest. <br>**Hinweis:** Legen Sie diesen Wert fest, um Kontoinformationen abzurufen. <br>Erfolgt keine Angabe für diesen Parameter, wird der Standardwert für den aktuellen Bereich auf *-1* festgelegt. Dabei handelt es sich um den Bereich, an dem Sie sich mit dem Befehl `cf login` angemeldet haben. </dd>
</dl>

**Beispiele**

Um den aktuellen Aufbewahrungszeitraum für den Bereich anzuzeigen, bei dem Sie angemeldet sind, führen Sie den folgenden Befehl aus:

```
cf logging option
```
{: codeblock}

Die Ausgabe sieht wie folgt aus:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| d35da1e3-b345-475f-8502-cfgh436902a3 |        30 |
+--------------------------------------+-----------+
```
{: screen}


Um den Aufbewahrungszeitraum für den Bereich, bei dem Sie angemeldet sind, in 25 Tage zu ändern, führen Sie den folgenden Befehl aus:

```
cf logging option -r 25
```
{: codeblock}

Die Ausgabe sieht wie folgt aus:

```
+--------------------------------------+-----------+
|               SPACEID                | RETENTION |
+--------------------------------------+-----------+
| d35da1e3-b345-475f-8502-cfgh436902a3 |        25 |
+--------------------------------------+-----------+
```
{: screen}


## cf logging session create (Beta)
{: #session_create}

Mit diesem Befehl können Sie eine neue Sitzung erstellen.

**Hinweis:** Sie können bis zu 30 Sitzungen in einem Bereich gleichzeitig ausführen. Die Sitzung wird für einen Benutzer erstellt. Sitzungen können nicht von verschiedenen Benutzern in einem Bereich gemeinsam genutzt werden.

```
cf logging session create [Parameter]
```
{: codeblock}

**Parameter**

<dl>
  <dt>--start Wert, -s Wert</dt>
  <dd>(Optional) Legt das Startdatum in koordinierter Weltzeit (UTC) fest: *JJJJ-MM-TT*, z. B. `2006-01-02`. <br>Der Standardwert ist auf 'vor zwei Wochen' festgelegt.
  </dd>
  
  <dt>--end Wert, -e Wert</dt>
  <dd>(Optional) Legt das Enddatum in koordinierter Weltzeit (UTC) fest: *JJJJ-MM-TT*, z. B. `2006-01-02`. <br>Der Standardwert wird auf das aktuelle Datum gesetzt.
  </dd>
  
  <dt>--type Wert, -t Wert</dt>
  <dd>(Optional) Legt den Protokolltyp fest. <br>Ein Protokolltyp ist beispielsweise *syslog*. <br>Standardwert ist ein Stern (*). <br>Sie können mehrere Protokolltypen angeben, indem Sie die einzelnen Typen durch Kommas trennen. Beispiel: *log_type_1,log_type_2,log_type_3*.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Optional) Legt den Geltungsbereich auf Kontoebene fest. <br>**Hinweis:** Legen Sie diesen Wert fest, um Kontoinformationen abzurufen. <br>Erfolgt keine Angabe für diesen Parameter, wird der Standardwert nur auf den aktuellen Bereich gesetzt. Dabei handelt es sich um den Bereich, bei dem Sie sich mit dem Befehl `cf login` angemeldet haben.
  </dd>
</dl>

**Zurückgegebene Werte**

<dl>
<dt>Access-Time</dt>
<dd>Zeitmarke, die angibt, wann die Sitzung zum letzten Mal verwendet wurde.</dd>

<dt>Create-Time</dt>
<dd>Zeitmarke des Zeitpunkts (Datum und Uhrzeit), als die Sitzung erstellt wurde.</dd>

<dt>Date-Range</dt>
<dd>Gibt den Datumsbereich (Tage) an, der verwendet wird, um Protokolle zu filtern. Die Protokolle, die in diesem Datumsbereich ermittelt werden, können über die Sitzung verwaltet werden.</dd>

<dt>ID</dt>
<dd>Sitzungs-ID. </dd>

<dt>Space</dt>
<dd>ID des Bereichs, für den die Sitzung aktiv ist.</dd>

<dt>Type-Account</dt>
<dd>Protokolltypen, die über die Sitzung heruntergeladen werden.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}} ID des Benutzers, der die Sitzung erstellt hat.</dd>
</dl>


**Beispiel**

Führen Sie den folgenden Befehl aus, um eine Sitzung zu erstellen, in der Protokolle vom 20. Mai 2017 bis zum 26. Mai 2017 für den Protokolltyp *log* enthalten sind. 

```
cf logging session create -s 2017-05-20 -e 2017-05-26 -t log
```
{: screen}


## cf logging session delete (Beta)
{: #session_delete}

Löscht eine Sitzung, die durch die Sitzungs-ID angegeben ist.

```
cf logging session delete [Argumente]
```
{: codeblock}

**Argumente**

<dl>
<dt>session ID</dt>
<dd>ID der Sitzung, die Sie löschen wollen. <br>Mit dem Befehl `cf logging session list` können Sie alle aktiven Sitzungs-IDs abrufen.</dd>
</dl>

**Beispiel**

Um eine Sitzung mit der Sitzungs-ID *cI6hvAa0KR_tyhjxZZz9Uw==* zu löschen, führen Sie den folgenden Befehl aus:

```
cf logging session delete cI6hvAa0KR_tyhjxZZz9Uw==
```
{: screen}



## cf logging session list (Beta)
{: #session_list}

Listet die aktiven Sitzungen und ihre IDs auf.

```
cf logging session list 
```
{: codeblock}

**Zurückgegebene Werte**

<dl>
<dt>ID</dt>
<dd>Sitzungs-ID. </dd>

<dt>SPACE</dt>
<dd>ID des Bereichs, für den die Sitzung aktiv ist.</dd>

<dt>USERNAME</dt>
<dd>{{site.data.keyword.IBM_notm}} ID des Benutzers, der die Sitzung erstellt hat.</dd>

<dt>CREATE-TIME</dt>
<dd>Zeitmarke des Zeitpunkts (Datum und Uhrzeit), als die Sitzung erstellt wurde. </dd>

<dt>ACCESS-TIME</dt>
<dd>Zeitmarke, die angibt, wann die Sitzung zum letzten Mal verwendet wurde. </dd>
</dl>
 

## cf logging session show (Beta)
{: #session_show}

Zeigt den Status einer einzelnen Sitzung.

```
cf logging session show [Argumente]
```
{: codeblock}

**Argumente**

<dl>
<dt>session_ID</dt>
<dd>ID der aktiven Sitzung, für die Sie Informationen abrufen möchten.</dd>
</dl>

**Zurückgegebene Werte**

<dl>
<dt>Access-Time</dt>
<dd></dd>

<dt>Create-Time</dt>
<dd>Zeitmarke des Zeitpunkts (Datum und Uhrzeit), als die Sitzung erstellt wurde.</dd>

<dt>Date-Range</dt>
<dd>Gibt den Datumsbereich (Tage) an, der verwendet wird, um Protokolle zu filtern. Die Protokolle, die in diesem Datumsbereich ermittelt werden, können über die Sitzung verwaltet werden.</dd>

<dt>ID</dt>
<dd>Sitzungs-ID. </dd>

<dt>Space</dt>
<dd>ID des Bereichs, für den die Sitzung aktiv ist.</dd>

<dt>Type-Account</dt>
<dd>Protokolltypen, die über die Sitzung heruntergeladen werden.</dd>

<dt>Username</dt>
<dd>{{site.data.keyword.IBM_notm}} ID des Benutzers, der die Sitzung erstellt hat.</dd>
</dl>

**Beispiel**

Um Details zu einer Sitzung mit der Sitzungs-ID *cI6hvAa0KR_tyhjxZZz9Uw==* anzuzeigen, führen Sie den folgenden Befehl aus:

```
cf logging session show cI6hvAa0KR_tyhjxZZz9Uw==
```
{: screen}


## cf logging status
{: #status}

Verwenden Sie diesen Befehl, um Informationen zu den Protokollen abzurufen, die in einem {{site.data.keyword.Bluemix_notm}}-Bereich oder -Konto erfasst werden.

```
cf logging status [Parameter]
```
{: codeblock}

**Parameter**

<dl>
  <dt>--start Wert, -s Wert</dt>
  <dd>(Optional) Legt das Startdatum in koordinierter Weltzeit (UTC) fest: *JJJJ-MM-TT*, z. B. `2006-01-02`. <br>Der Standardwert ist auf 'vor zwei Wochen' festgelegt.
  </dd>
  
  <dt>--end Wert, -e Wert</dt>
  <dd>(Optional) Legt das Enddatum in koordinierter Weltzeit (UTC) fest: *JJJJ-MM-TT*, z. B. `2006-01-02`. <br>Der Standardwert wird auf das aktuelle Datum gesetzt.
  </dd>
  
  <dt>--type Wert, -t Wert</dt>
  <dd>(Optional) Legt den Protokolltyp fest. <br>Ein Protokolltyp ist beispielsweise *syslog*. <br>Standardwert ist ein Stern (*). <br>Sie können mehrere Protokolltypen angeben, indem Sie die einzelnen Typen durch Kommas trennen. Beispiel: *log_type_1,log_type_2,log_type_3*.
  </dd>
  
  <dt>--at-account-level, -a </dt>
  <dd>(Optional) Legt den Geltungsbereich auf Kontoebene fest. <br> **Hinweis:** Legen Sie diesen Wert fest, um Kontoinformationen abzurufen. <br>Erfolgt keine Angabe für diesen Parameter, wird der Standardwert nur auf den aktuellen Bereich gesetzt. Dabei handelt es sich um den Bereich, bei dem Sie sich mit dem Befehl `cf login` angemeldet haben.
  </dd>
  
  <dt>--list-type-detail, -l</dt>
  <dd>(Optional) Legen Sie diesen Parameter fest, um das Zwischenergebnis der Protokolltypen für jeden Tag aufzulisten.
  </dd>
</dl>

**Hinweis:** Der Befehl `cf logging status` meldet nur die Protokolle der letzten beiden Wochen, die in 'Log Collection' gespeichert sind, wenn kein Start- und Enddatum angegeben ist.


