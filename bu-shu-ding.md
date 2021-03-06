---
description: 本節包含，如何從外部連到 Container、如何掛載 Volume、device
---

# 詳細部署設定

## Access to Container

### 1. NodePort

#### 設定 NodePort 可以讓你從你的電腦連線到 Container

在建立 Container 的時候指定，或編輯 Port 欄位

| Container Port | Protocol | Type | Port on Node |
| :--- | :--- | :--- | :--- |
| Container 上的 Port | TCP or UDP | NodePort | 對外 Port |

![container &#x4E0A;&#x7684; 80 &#x5C0D;&#x4E0A;&#x4E00;&#x500B;&#x96A8;&#x6A5F;&#x7684; port \(30000 - 32767\)](.gitbook/assets/1.png)

完成後，回到 Workloads 頁面，會看到底下的 `30189/TCP` 點它後，跳出的新網頁，網址列上的 ip: port 就可以連到 Container 上

![](.gitbook/assets/image%20%2826%29.png)

### 2. Ingress

#### 設定 Domain name 

{% hint style="warning" %}
只支援 HTTP\(S\) 協定
{% endhint %}

#### 到左上角 Cluster:xxx -&gt; Project:xxx 右邊的 Workloads 下方的 Load Balancing 

按右上角 `Add Ingress`

![](.gitbook/assets/2.PNG)

設定 Name, 所屬 Namespace, Rules 選第一個 `Automatically generate`Target 選要對應到的 workloads 和 container port

{% hint style="info" %}
也可以自己指定 Domain name \(需自行設定 hosts 對應到任一個 node 的 ip\)
{% endhint %}

![](.gitbook/assets/image%20%2822%29.png)

透過生成的 Domain name 可以連到網頁上

![](.gitbook/assets/image%20%286%29.png)

![](.gitbook/assets/image%20%2814%29.png)

## Volume 設定

#### 因為 Container 啟動後新增的資料，在 Container 重啟或刪除後並不會被保存下來，若要保存資料，需要掛上 NFS 的  Volume ，如此資料才會被保存下來

### 新增 Volume

到 Workloads 找到要掛 volume 的 Container 按右邊三的點 -&gt; Edit

![](.gitbook/assets/image%20%2813%29.png)

新增 volume \(Add volume... -&gt; Add a persistent volume\)

![](.gitbook/assets/1.PNG)

![](.gitbook/assets/2%20%281%29.PNG)

設定位置、空間大小、_**Storage Class**_、Access Mode 完成後，按 Define

{% hint style="info" %}
Source 選 Use a Storage Class to provision a new persistent volume ，右邊 Storage Class 選任一個，按 Define
{% endhint %}

![](.gitbook/assets/3%20%281%29.PNG)

指定 Mount Path \( volume 在 Container 中的目錄位置\)，完成後按 Update

![](.gitbook/assets/4%20%281%29.PNG)

 狀態變為 Avtice 就成功了

![](.gitbook/assets/image%20%2818%29.png)

若要找已經建立好的 Volume，可以按 Workloads 右方的 Volume 頁面找到

![](.gitbook/assets/333.png)

{% hint style="info" %}
若需要存取 Volume 裡面的資料，要連到 NFS Server 上的 NFS 分享目錄下存取

資料夾在 NFS Server 上的命名規則為 "`<namespace>-<Volume Name>-pvc-xxxxxxxxxxxx`"    
這裡的例子會是 "`namespace02-vol01-pvc-xxxxxxxxxxxxx`" 可以在 NFS Server 設定的 Share directory 下找到這個資料夾
{% endhint %}

### 掛載之前的 Volume

若 Container 刪除後，Volume  

到 Workloads 找到要掛 volume 的 Container 按右邊三的點 -&gt; Edit

![](.gitbook/assets/image%20%2813%29.png)

掛載 volume \(Add volume... -&gt; Use an persistent volume\)

![](.gitbook/assets/image%20%287%29.png)

接著 Persistent Volume Claim 的下拉選單，可以選先前建立的 Volume，掛回 Container 中

![](.gitbook/assets/image%20%2825%29.png)

## Bind device

#### 把 Host 上的 /dev 目錄，底下的 device bind 到 Container 中

到 Workloads 找到要掛 device 的 Application 按右邊三的點-&gt; Edit

![](.gitbook/assets/image%20%2813%29.png)

按右下角 `show advance options`，找到 `Security & Host Config` 把 `Privileged` 選 yes

![](.gitbook/assets/tempsnip%20%285%29.png)

接著新增一個 Volume \(Add volume... -&gt; Bind mount a directory from the nodes\)

![](.gitbook/assets/1.PNG)

![](.gitbook/assets/image%20%2811%29.png)

設定名稱、node 上的 device 路徑\(Path on the node\)、container 上的路徑 \(Mount Path\)

![](.gitbook/assets/image%20%2818%29.png)

![](.gitbook/assets/image%20%2810%29.png)

完成後按最下面的 Upgrade，就完成了，可以到 container 底下找到 device

