# 建立 Namespace

{% hint style="danger" %}
在 Cluster:xxx, Project:xxx 不同階層，右方的 Navigation Bar 會功能會有所不同，要特別注意
{% endhint %}

## 建立新的 Namespace

到左上角 Global -&gt; Cluster:xxx 後，右方找到 Project/namespace Tab

進到頁面後，可以看到很多 namespace\(圖片裡有 Defaule 和 Project02\)

![](.gitbook/assets/tempsnip%20%283%29.png)



在任一個 Project:xxx 的右上角，按 Add Namespace

![](.gitbook/assets/image%20%2816%29.png)

設定名稱，完成後按 Create

![](.gitbook/assets/image%20%2819%29.png)

可看看到剛建立的 Namespace

![](.gitbook/assets/image%20%281%29.png)

{% hint style="warning" %}
同一個 Cluster 不可有相同名稱的 Namespace

Project01 底下有了 ns1，則 Project02 下不能再出現 ns1
{% endhint %}





