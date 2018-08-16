# 詳細部署設定

## Access to Container

### 1. NodePort

#### 所有節點都會開啟某個 port 對外

在建立 Container 的時候指定，或編輯 

| Container Port | Protocol | Type | Port on Node |
| :--- | :--- | :--- | :--- |
| Container 上的 Port | TCP or UDP | NodePort | 對外 Port |

![container &#x4E0A;&#x7684; 80 &#x5C0D;&#x4E0A;&#x4E00;&#x500B;&#x96A8;&#x6A5F;&#x7684; port \(30000 - 32767\) ](.gitbook/assets/3.PNG)

### 2. Ingress

#### 設定 Domain name 

{% hint style="warning" %}
只支援 HTTP\(S\) 協定
{% endhint %}

#### 到 Cluster:xxx -&gt; Project:xxx -&gt; Workloads -&gt; Load Balancing 的 Tab \(Wrkloads 右邊\)

按右上角 `Add Ingress`

![](.gitbook/assets/2.PNG)

設定 Name, 所屬 Namespace, Rules。  
Rules 選第一個 `Automatically generate`Target 選要對應到的 workloads 和 container port，  
也可以自己指定 Domain name \(需自行設定 hosts 對應到任一個 node 的 ip\)

![](.gitbook/assets/image%20%2820%29.png)

透過生成的 Domain name 可以連到網頁上

![](.gitbook/assets/image%20%285%29.png)

![](.gitbook/assets/image%20%2812%29.png)

## Volume 設定

#### 若要保存資料，需要掛上 NFS 的 Persistent Volume 

到 Workloads 找到要掛 volume 的 Container 按右邊三的點 -&gt; Edit

![](.gitbook/assets/image%20%2811%29.png)

新增 volume \(Add volume... -&gt; Add a persistent volume\)

![](.gitbook/assets/1.PNG)

![](.gitbook/assets/2%20%281%29.PNG)

設定位置、空間大小、Access Mode，  
Source 選 `Use a Storage Class to  provision a new persistent volume` 右邊 Storage 選一個`Storage Class` ，按 Define

![](.gitbook/assets/3%20%281%29.PNG)

指定 Mount Path \(在 Container 中的位置\)

![](.gitbook/assets/4%20%281%29.PNG)

最後 Update ，狀態變為 Avtice 就完成了

資料夾在 NFS Server 上的命名規則為 "`<namespace>-<Volume Name>-pvc-xxxxxxxxxxxx`"    
這裡的例子會是 "`namespace02-vol01-pvc-xxxxxxxxxxxxx`" 可以在 NFS Server 設定的 Share directory 下找到這個資料夾

## Bind device

#### 把 Host 上的 /dev 目錄，底下的 device bind 到 Container 中

到 Workloads 找到要掛 device 的 Application 按右邊三的點-&gt; Edit

![](.gitbook/assets/image%20%2811%29.png)

按右下角 `show advance options`，找到 `Security & Host Config` 把 `Privileged` 選 yes

![](.gitbook/assets/tempsnip%20%285%29.png)

接著新增一個 Volume \(Add volume... -&gt; Bind mount a directory from the nodes\)

![](.gitbook/assets/1.PNG)

![](.gitbook/assets/image%20%289%29.png)

設定名稱、node 上的 device 路徑\(Path on the node\)、container 上的路徑 \(Mount Path\)

![](.gitbook/assets/image%20%288%29.png)

完成後按最下面的 Upgrade，就完成了，可以到 container 底下找到 device

