---

copyright:
  years: 2017
lastupdated: "2017-07-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 仮想マシンのロギング
{: #logging_vm_ov}

ロギング機能は仮想マシン (VM) に対して自動的には有効になりません。しかし、ログを Log Collection に送信するよう VM を構成できます。VM からログ・データを収集して {{site.data.keyword.loganalysisshort}} サービスに送信するには、マルチテナント Logstash Forwarder (mt-logstash-forwarder) を構成する必要があります。そうすると、Kibana でログの表示、フィルタリング、および分析を行うことができます。
{:shortdesc}


## ログの取り込み
{: #log_ingestion}

{{site.data.keyword.loganalysisshort}} サービスにはさまざまなプランが用意されています。各プランでは、Log Collection にログを送信できるかどうかが定義されています。*ライト*・プランを除くすべてのプランには、Log Collection にログを送信する機能が含まれています。各種プランについて詳しくは、『[サービス・プラン](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans)』を参照してください。

mt-logstash-forwarder を使用することによって、ログを {site.data.keyword.loganalysisshort}} に送信できます。詳しくは、『[マルチテナント Logstash Forwarder (mt-logstash-forwarder) を使用したログ・データの送信](/docs/services/CloudLogAnalysis/how-to/send-data/send_data_mt.html#send_data_mt)』を参照してください。


## ログ収集
{: #log_collection}

デフォルトでは、{{site.data.keyword.Bluemix_notm}} はログ・データを最大 3 日間保管します。   

* スペースごとに 1 日に最大で 500 MB のデータが保管されます。500 MB の上限を超えるログは破棄されます。上限割り当ては、毎日午前 12:30 (UTC) にリセットされます。
* 1.5 GB までのデータを最大 3 日間検索可能です。ログ・データは、データが 1.5 GB に達するか 3 日が過ぎると、ロールオーバーします (先入れ先出し)。


{{site.data.keyword.loganalysisshort}} サービスには、必要な期間 Log Collection にログを保管できる追加プランがあります。各プランの料金について詳しくは、『[サービス・プラン](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans)』を参照してください。

Log Collection 内でログを保持する日数を定義するために使用できるログ保存ポリシーを構成できます。詳しくは、『[ログ保存ポリシー](/docs/services/CloudLogAnalysis/log_analysis_ov.html#policies)』を参照してください。


## ログ検索
{: #log_search}

デフォルトでは、{{site.data.keyword.Bluemix_notm}} では、1 日当たり 500 MB までのログを Kibana を使用して検索できます。 

{{site.data.keyword.loganalysisshort}} サービスには複数のプランが用意されています。ログ検索の機能はプランによって異なります。例えば、*ログ収集*プランでは、1 日当たり 1 GB までのデータを検索できます。各種プランについて詳しくは、『[サービス・プラン](/docs/services/CloudLogAnalysis/log_analysis_ov.html#plans)』を参照してください。


## ログ分析
{: #log_analysis}

ログ・データを分析するには、Kibana を使用して高度な分析タスクを実行します。分析および視覚化のためのオープン・ソース・プラットフォームである Kibana を使用して、さまざまなグラフ (図表や表など) でデータのモニター、検索、分析、および視覚化を行うことができます。詳しくは、『[Kibana でのログの分析](/docs/services/CloudLogAnalysis/kibana/analyzing_logs_Kibana.html#analyzing_logs_Kibana)』を参照してください。
