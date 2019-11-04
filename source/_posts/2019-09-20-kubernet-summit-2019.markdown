---
layout: post
title: "Kubernet Summit 2019"
date: 2019-09-20 18:04:14 +0800
comments: true
categories: k8s
---

### 簡易重點

1. 賣 K8s 的人不敢告訴你的事 - 葉秉哲（William）
    * 導入前必須提出的問題：維運成本、拓展性、管理性
    * 供應商提供的數據是否符合現實需求
    * 現有架構是否已經完成解耦合微服務化，已適合搬遷
    * 配套CI/CD與分散式log收集監視是否完備

<!--more-->

2. 跨雲不受限─新一代開放式企業混合雲原生平台 - 彭信忠（Jason Peng）
    * Openshit 提供的是基於容器技術提供一個跨雲的平台
    * K8S 不是一個產品，也不是一個完整的技術他只是一個框架
    * K8S 只是做為容器調度和集群管理的角色
    * 中華電信案例：
        * scaling 所產生的費用問題
        * Rest API 方便擴充
        * Pod 串太長影響效率
        * 搬遷注意事項（軟體 License、kernel 版本、Volume Problem）

3. BM's Kubernetes Journey: Community Contributions, Key Applications, and our Cloud Native Transformation Strategy - Dr. Brad Topol

    * IBM在虛擬容器社群的投資與貢獻
    * Tekton：Pipelines 提供k8s CI/CD功能（用以取代Jenkins）
    * Razee : 將各叢集、環境和雲端提供者之間的 Kubernetes 資源部署自動化並予以管理
    * 與國際組織發起Call for Code 以科技方針因應自然災害案例

4. 邁向多 K8s 的旅程─powered by CNCF 的 Cluster API - 何宗憲
    * Cluster API
    * Kubenetes 開發快，但佈建問題很多
    * Cluster API 兩種生成方式：現有叢集 & Pivotal Workflow
    * 標準結合了K8s與公有雲+ 私有雲
    * Kubenetes is a platform, not only container

5. Docker Swarm 太陽春 K8s 太複雜？試試輕量級的 K3s 吧！ - 王偉任（Weithenn
    * k3s現場demo
        * 以 containerd (預設) 取代 docker (選用)，習慣用 docker: 安裝時 --docker
        * 可配合 Rancher 使用
        * 到了 2020, 80% Container 是跑在 VM 裡面
        * 用 VM run 的服務是 stateful, container 是 stateless
        * 前端 web service 很適合做 container

6. Harden Your Kubernetes Cluster - 蔡宗城（smalltown）

    * Security 層面上 Kubernetes 本身並不會去多做什麼
    * Image Build Practice (映像檔建置原則;實用)
        * Minimal Base Images
        * Least Privileged User
        * Use Fixed Tags
        * Sign/Verify Images
        * Don’t Contain Sensitive Information
        * Use COPY Instead of ADD
        * Use Metadata Labels
        * Multi-Stage Build Small/Secure Images
        * nd/Fix/Monitor Vulnerabilities
    * Authentication: 常見token, auth 技巧
    * Dynamic Credentials 動態憑證
    * Ingress 需設定阻隔他人竊聽

7. 前方有雷別再踩─企業導入 Kubernetes 的掃雷指南 - 朱培華
    * 以系統維運工師角度需讓程式開發者有基本的物件觀念
        * 了解如何使用 DNS 名稱存取服務 (Service)
        * 了解滾動升級的過程 (Rolling Update)
        * 討論如何讓 Kubernetes 判斷程式的狀態 (Liveness/Readiness Probe)
        * 讓他們知道更新 ConfigMap 不會自動套用到 Pod 上 (ConfigMap)
    * YAML
        * 內容越精簡越好，多使用預設值 (Default)
        * 使用版控將每一版的 YAML 都儲存下來
        * kubectl apply 前務必檢視過一次 YAML 的內容

    * 各種經驗談（炸硬碟, 炸cpu, 炸記憶體等等）
    * 監控與記錄檔收集服務（例如: ELK, Grafana）

8. 使用 Kubernetes 打造企業級應用系統 - 李日貴（Gary）
    * 利用IBM Cloud Private 在3公司 建立K8s 為基礎的私有雲
        * 不是很想接觸native 的環境，因為要負全責...
    * 沒有規範的Log是沒有意義的

### 應用

本次以開發工程師角度前往了解kubernetes運維與部署實例，再次驗證了當前以結合系統容器結合服務開發是當前與未來的主流趨勢，故同時擁有開發技巧與容器部署的DevOps角色是我認為優秀後端人員努力的方向。

* 應用場景：
    * 易拓展特性(Scalling)適合有活動才大量需要資源的服務，或短時間需要大量效能的服務
    * ConfigMap 可解決至當前LG單純電子打包設定值需重啟的問題
    * 公有混私有雲的部分可進一步控制整體硬體維運成本
    * 善用Tekton 類型CI/CD套件可減少系統與人為疏失，提高服務品質與軟體信心
    * ELK 數據收集分析軟體，短期可有效整合異質平台log，長期可用予系統效能分析與用戶習慣分析

K8S 不是一個產品，也不是一個完整的技術他只是一個框架。各講者無不提醒我們kubernetes不是萬靈丹，不是特效藥，而是一個可將服務靈活拓展的巨大框架，故“導入”的過程中必定伴隨著一定的轉換成本，可能是套件的抽換、系統的解偶、人員的訓練至成本的重新評估，但相信在滿足各項條件且克服轉換困難後，可比肩一流軟體服務開發企業的研發能量與穩定品質
