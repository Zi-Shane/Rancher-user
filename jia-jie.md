---
description: Rancher2.0 架構
---

# 架構介紹

## 架構

* Cluster
  * Project
    * Namespace
      * Container, volume...... 

Cluster 可以開多個 Project

Project 底下可以有一個或多個 Namespace

所有 Container 和 volume 等資源，都會屬於某一個 Namespace

#### 一個 Container 可以跑一個 Nginx, MySQL, Solr, Apache, Tomcat......

## Cluster

#### 由一群電腦組成一個 Cluster

登入之後可看到，所有可以使用的 Kubernetes 叢集

這裡有兩個 Cluster 分別是 Cluster01和 Cluster02

![&#x767B;&#x5165;&#x4E4B;&#x5F8C;&#x53EF;&#x770B;&#x5230;&#x53EF;&#x7528;&#x7684; Cluster](.gitbook/assets/image%20%2820%29.png)

## Project

#### 一個 Cluster 可以分成多個不同 Project

左上角 Global -&gt; Cluster:xxx 底下為可用的 project 

這裡有兩個 Project 在 Cluster01 底下，分別是 Default 和 Project02

![Cluster &#x53EF;&#x5206;&#x591A;&#x500B; Project &#x4F7F;&#x7528;](.gitbook/assets/image%20%283%29.png)

## Namespace

#### Project 底下可以再分多個 Namespace

進入左上角 Global -&gt; Cluster:xxx -&gt; Projectxx 後，再分為多的 Namespace，Namespace 底下可以部署 Container

![Project &#x5E95;&#x4E0B;&#x7684; Namespace](.gitbook/assets/image%20%2829%29.png)

{% hint style="danger" %}
Cluster, Project, Namespace 由左上角的 Rancher Logo 右方的 Dropdown 下拉選單切換

之後都將以 Cluster:xxx -&gt; Project:xxx 這樣的形式作為指引 ;  
意思是 Cluster:xxx 底下的 Project:xxx 
{% endhint %}





