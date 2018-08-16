---
description: 部署一個簡單的 Nginx 為範例
---

# 部署 Container

### Step1:  進入 Workloads 頁面

#### 進入 Cluster -&gt; Project -&gt; Workloads 後，右上角兩種方法 Import YAML 或 Deploy  

![](.gitbook/assets/tempsnip%20%282%29.png)

### Step2: 設定 Container 資訊

####     選  Import YAML：

        匯入已有的 YAML

####     選  Deploy：

        依照需求，設定 Container 資訊 ，Name、Port、Environmant Variables、 Volume...

![&#x8F38;&#x5165; name&#x3001;Image&#x3001;&#x5C6C;&#x65BC;&#x54EA;&#x500B; Namesapce&#xFF0C;port &#x7B49;&#x8CC7;&#x8A0A;](.gitbook/assets/image%20%2813%29.png)

  
下方可設定 ENV、Volume 等......

![](.gitbook/assets/image%20%2824%29.png)

{% hint style="info" %}
#### 詳細設定

* [Access to Container](bu-shu-ding.md#access-to-container)
* [Volume](bu-shu-ding.md#volume-ding)
* [Bind device](bu-shu-ding.md#bind-device)
{% endhint %}

### Step3: 完成

#### 成功部署完成後，會顯示 Acvtive 

![](.gitbook/assets/image%20%2816%29.png)

若有設定 Port 可以點選底下的 `30189/TCP`透過 HTTP 連到網頁上。

![](.gitbook/assets/image%20%2823%29.png)

### 修改設定

按右側的 三個點 -&gt; Edit

![](.gitbook/assets/image%20%2811%29.png)

