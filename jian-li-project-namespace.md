# 建立 Project, Namespace

## 建立新的 Project

到 Global -&gt; Cluster:xxx 後，右方找到 Project/namespace Tab

進到頁面後，右上角會有 Add Project

![](.gitbook/assets/tempsnip%20%283%29.png)

輸入名稱、設定可存取的 Member 後，按 Create 就完成了

![](.gitbook/assets/image%20%2825%29.png)

完成後，到左上角 Global -&gt; Cluster:xxx 底下就可以看到剛建立的 Project

## 建立新的 Namespace

到 Global -&gt; Cluster:xxx 後，右方找到 Project/namespace Tab，在任一個 Project 的右上角，按 Add Namespace

![](.gitbook/assets/image%20%2814%29.png)

設定名稱、屬於哪個 Project，按 Create，就完成了

![](.gitbook/assets/image%20%2817%29.png)

{% hint style="warning" %}
同一個 Cluster 不可有相同名稱的 Namespace

Project01 底下有了 ns1，則 Project02 下不能再出現 ns1
{% endhint %}





